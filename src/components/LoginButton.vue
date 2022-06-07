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
        username: "Admin",
        password: "Admin",
      });

      var config = {
        method: "post",
        url: "https://localhost:8443/login",
        headers: {
          "Access-Control-Allow-Origin" : "*",
          "Content-Type": "application/json",
          "Accept": "*/*", 
          "Conntection": "keep-alive",
        },
        withCredentials: true, 
        data: data,
      };

      axios(config)
        .then((response) => console.log(response.headers["set-cookie"]))
    },
  },
};
</script>
