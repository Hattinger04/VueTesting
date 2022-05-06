<template>
  <div class="container">
    <h1>{{ msg }}</h1>
    <Button />
    <RestButton name="Get Rest" link="http://127.0.0.1:8081/user/getAllUsers" method="GET"/>
    <RestButton name="Post Rest" link="http://127.0.0.1:8081/user/createUser" method="POST" :data=sendData />
  </div>
</template>

<script>
import Button from "./Button.vue";
import RestButton from "./RestButton.vue";
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
      }
    };
  },
  props: {
    msg: {
      type: String,
      default: "Hallo Welt",
    },
  },
  components: {
    Button,
    RestButton,
  },
};
</script>

<style scoped>
div {
  height: 100%;
}
</style>
