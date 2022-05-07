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
    data: {
      type: Array,
      default: {},
    },
  },
  methods: {
    // TestURL: https://gorest.co.in/public/v2/users
    async clickevent() {
      var data = new URLSearchParams();
      Object.entries(this.data).forEach(([key, value]) => {
        data.append(key, value);
      });
      console.log(data.toString());
      await fetch(this.link, {
        headers: {
          "Content-Type": "application/x-www-form-urlencoded;charset=UTF-8",
        },
        mode: "cors",
        method: this.method,
        body: this.method == this.html_methods.GET ? null : JSON.stringify(data),
      })
        .then((response) => response.json())
        .then((json) => (this.get = json));
    },
  },
};
</script>
