<template>
    <div class="container">

        <h1>System do zapisów na zajęcia</h1>

        <div v-if="authenticatedUsername !== ''">
            <logout-form @logout="logMeOut()"></logout-form>
        </div>

        <div v-else>
            <login-form @login="logMeIn($event)"></login-form>
        </div>

        <meeting-page v-show="authenticatedUsername" :username="authenticatedUsername"></meeting-page>

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
