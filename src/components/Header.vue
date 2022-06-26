<template>
  <div class="container">
    <h1>Rest - Example - Buttons</h1>
     <!-- Of cource you have to change the ip from localhost to the server-ip address 
     but you dont have to change smth in nginx - is tested! -->
    <RestButton name="Get All users" link="https:/localhost/api/user/getAllUsers" method="get"/>
    <RestButton name="Create new user" link="https:/localhost/api/user/createUser" method="post" :data=sendData />
    <LoginButton link="https://localhost/api/login" :data=sendLogin />
    <RestButton name="Run Default Hamster" link="https://localhost/api/hamster/defaultTerrain" method="post" :data=sendDefaultHamster />
    <RestButton name="Logout" link="https://localhost/api/user/logout" method="get"/>
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
        "username": "admin", 
        "password": "admin",
      },
      sendDefaultHamster: {
        "programName": "vuetest",
        "program": "void main() { linksUm();}",
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
