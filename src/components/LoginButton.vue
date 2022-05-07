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
      type: Array,
      default: {},
    },
  },
  methods: {
    // TestURL: https://gorest.co.in/public/v2/users
    clickevent() {
      axios.post(
          this.link,
          new URLSearchParams({
            username: "Admin",
            password: "Admin",
          }),
          {
            headers: {
              Accept: "application/json",
              "Content-Type": "application/json",
            },
          }
        )
        .then((response) => (this.get = response));
    },
  },
};
</script>
