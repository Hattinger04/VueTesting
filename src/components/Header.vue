<template>
    <div class="container">
        <h1>{{ msg }}</h1>
        <Button/>
    </div>
</template>


<script>
import Button from './Button.vue'
    export default {
        name: 'Header',
        data() {
            return {
                hello : 'Hallo'
            }
        },
        props: {
            msg : {
                type: String,
                default : 'Hallo Welt'
            }
        }, 
        components : {
            Button
        }
    }
</script>

<style scoped>
    div{
        height: 100%;
    }
</style>