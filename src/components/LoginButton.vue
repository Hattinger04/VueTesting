<template>
  <div class="container">
    <button @click="clickevent()" class="btn" v-text="name"></button>
    <p>{{ get }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "RestButton",

  data() {
    return {
      get: null,
    };
  },
  props: {
    name: {
      type: String,
      default: "Login Button",
    },
    link: {
      type: String,
      default: "",
    },
    data: {
      type: Object,
      default: {},
    },
  },
  methods: {
    // TestURL: https://gorest.co.in/public/v2/users
    async clickevent() {
      axios.defaults.withCredentials=true; 
      var data = JSON.stringify({
        username: "Hattinger04",
        password: "Hattinger04",
      });
      var config = {
        method: "post",
        url: this.link,
        headers: {
          "Access-Control-Allow-Origin" : "*",
          "Content-Type": "application/json",
          "Accept": "*/*", 
        },
        withCredentials: true, 
        data: data,
      };

      axios(config)
        .then((response) => this.get = "logged in")
        .catch(error => this.get = "not logged in")
    },
  },
};
</script>
