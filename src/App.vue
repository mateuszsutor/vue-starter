<template>
    <div>

        <div v-if="authenticatedUsername != ''">
            <h3 v-if="authenticatedUsername">Jestes zalogowany jako: {{email}}</h3>
            <a @click="logMeOut">Wyjdz</a>
        </div>
        <div v-else>
            <h1>Witaj w systemie do zapisów na zajęcia</h1>
            <p>Zaloguj się e-mailem</p><input type="email" v-model="email">
            <button @click="logMeIn">Wchodzę</button>
        </div>


    </div>
</template>

<script>
    import HelloWorld from './components/HelloWorld.vue'

    export default {
        data() {
            return {
                email: '',
                authenticatedUsername: ''
            };
        },
        methods: {
            logMeIn() {
                this.authenticatedUsername = this.email,
                this.email = ''
            },
            logMeOut(){
                this.authenticatedUsername = '';

            }

        }
    }
</script>

<style>

</style>
