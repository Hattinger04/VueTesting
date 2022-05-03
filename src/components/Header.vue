<template>
    <div class="container">
        <h1>{{ msg }}</h1>
        <Button/>
        <RestButton v-bind:name="name" v-bind:method="method" v-bind:link="link"/>
    </div>
</template>


<script>
import Button from './Button.vue'
import RestButton from "./RestButton.vue"
    export default {
        name: 'Header',
        data() {
            return {
                name: "Hallo",
                method: "GET", 
                link: "localhost:8080/user"
            }
        },
        props: {
            msg : {
                type: String,
                default : 'Hallo Welt'
            }
        },
        components : {
            Button, RestButton
        }
    }
</script>

<style scoped>
    div{
        height: 100%;
    }
</style>