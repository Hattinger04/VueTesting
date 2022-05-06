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
      default: "Login Button",
    },
    link: {
      type: String,
      default: "",
    },
    data: {
      type: Array, 
      default: {},
    }
  },
  methods: {
    // TestURL: https://gorest.co.in/public/v2/users
    async clickevent() {
      let formData = new FormData();
      Object.entries(this.data).forEach(([key, value]) => {
        formData.append(key, value);
      });
      await fetch(this.link, {
        mode: "cors", 
        method: "POST",
        body: formData
      })
        .then((response) => response.json())
        .then((json) => (this.get = json));
    },
  },
};
</script>
