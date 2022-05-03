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
      html_methods: {
        GET: "GET",
        POST: "POST",
        PATCH: "PATCH",
        PUT: "PUT",
        DELETE: "DELETE",
      },
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
    method: {
      type: String,
      default: "",
    },
  },
  methods: {
    // TestURL: https://gorest.co.in/public/v2/users
    async clickevent() {
      await fetch(this.link, {
        method: this.method,
        body:
          this.method == this.html_methods.GET
            ? null
            : JSON.stringify(this.data),
      })
        .then((response) => response.json())
        .then((data) => (this.get = data));
    },
  },
};
</script>
