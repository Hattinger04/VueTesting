<template>
    <button @click="clickevent()" class="btn" v-text="name"></button>
</template>

<script>

export default {
    name: "RestButton", 
    
    props: {
        name : {
            type: String, 
            default: "Rest Button"
        },
        link : {
            type: String, 
            default: ""
        }, 
        data : {
            type: String, 
            default: ""
        },
        method : {
            type: String, 
            default: "GET"
        }
    }, 
    methods: {
        async clickevent() {
            await fetch(this.link, {
                method: this.method, 
                body: JSON.stringify(this.data)
            })
            .then(response => response.json())
            .then(data => alert(data))
        }
    }
}
</script>
