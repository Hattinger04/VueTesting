<template>
  <div class="container">
    <h1>{{ msg }}</h1>
    <Button />
    <RestButton name="Get Rest" link="https://gorest.co.in/public/v2/users" method="GET"/>
  </div>
</template>

<script>
import Button from "./Button.vue";
import RestButton from "./RestButton.vue";
export default {
  name: "Header",
  data() {
    return {
      
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
