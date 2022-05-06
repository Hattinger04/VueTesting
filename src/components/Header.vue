<template>
  <div class="container">
    <h1>Rest - Example - Buttons</h1>
    <RestButton name="Get All users" link="http://localhost:8081/user/getAllUsers" method="GET"/>
    <RestButton name="Create new user" link="http://127.0.0.1:8081/user/createUser" method="POST" :data=sendData />
    <LoginButton link="http://localhost:8081/user/login" :data=sendLogin />
  </div>
</template>

<script>
import Button from "./Button.vue";
import RestButton from "./RestButton.vue";
import LoginButton from "./LoginButton.vue"

export default {
  name: "Header",
  data() {
    return {
      sendData: {
        "username": "vuetest", 
        "password": "vuetest", 
        "email": "vuetest@tsn.at", 
        "name": "vuetest", 
        "lastName": "vuetest", 
        "active": "true", 
      }, 
      sendLogin: {
        "username": "Admin", 
        "password": "Admin"
      }
    };
  },
  props: {
  },
  components: {
    Button,
    RestButton,
    LoginButton,
  },
};
</script>

<style scoped>
div {
  height: 100%;
}
</style>
