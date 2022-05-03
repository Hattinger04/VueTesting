<template>
    <div class="container">
        <h1>{{ msg }}</h1>
        <Button/>
        <RestGetButton v-bind:name="name" v-bind:link="link"/>
    </div>
</template>


<script>
import Button from './Button.vue'
import RestGetButton from "./RestGetButton.vue"
    export default {
        name: 'Header',
        data() {
            return {
                name: "Get Rest",
                link: "https://gorest.co.in/public/v2/users"
            }
        },
        props: {
            msg : {
                type: String,
                default : 'Hallo Welt'
            }
        },
        components : {
            Button, RestGetButton
        }
    }
</script>

<style scoped>
    div{
        height: 100%;
    }
</style>