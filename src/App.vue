<template>
    <div class="container">

        <h1>Witaj w systemie zapisów na zajecia</h1>

        <div v-if="authenticatedUsername != ''">
            <logout-form @logout="logMeOut($event)" ></logout-form>
            <meeting-page></meeting-page>

        </div>

        <div v-else>
            <login-form @login="logMeIn($event)" ></login-form>
        </div>

    </div>

</template>

<script>
    import "milligram";
    import LoginForm from "./loginData/LoginForm";
    import LogoutForm from "./loginData/LogoutForm";
    import MeetingPage from "./meetings/MeetingPage";


    export default {
        components: {LoginForm, MeetingPage, LogoutForm},
        data() {
            return {
                authenticatedUsername: ''
            };
        },
        methods: {
            logMeIn(username) {
                this.authenticatedUsername = username;

            },
            logMeOut() {
                this.authenticatedUsername = ''
            }

        }
    }
</script>

<style>

</style>
