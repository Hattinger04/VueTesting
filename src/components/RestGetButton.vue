<template>
  <div class="container">
    <button @click="clickevent()" class="btn" v-text="name"></button>
    <p>{{ get }}</p>
  </div>
</template>

<script>
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
      default: "Rest Get Button",
    },
    link: {
      type: String,
      default: "",
    },
  },
  methods: {
      // TestURL: https://gorest.co.in/public/v2/users
    async clickevent() {
      await fetch(this.link, {
        method: "GET",
      })
        .then((response) => response.json())
        .then((data) => (this.get = data));
    },
  },
};
</script>
