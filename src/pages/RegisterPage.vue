<template>
    <div id="register-page">
        <button @click="logIn()">Log in</button>
    </div>
</template>

<script>

export default{
    data(){

    },
    methods:{
        logIn(){
            this.$router.push("/indexpage")
        }
    },
    router: {
    base: '/',
    middleware: 'home'
  }
}
</script>