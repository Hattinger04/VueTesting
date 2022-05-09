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
    clickevent2() {
      var querystring = require("querystring");
      axios
        .post(
          this.link,
          querystring.stringify({
            username: "Admin",
            password: "Admin",
          }),
          {
            headers: {
              "Content-Type": "application/x-www-form-urlencoded",
            },
          }
        )
        .then((response) => (this.get = JSON.parse(response)));
    },
    async clickevent() {
      let formData = new FormData();
      formData.append("username", "Admin");
      formData.append("password", "Admin");
      await fetch(this.link, {
        method: "POST",
        body: formData,
      })
        .then(function (response) {
          return response.body;
        })
        .then(blob => this.get = URL.createObjectURL(blob));
    },
  },
};
</script>
