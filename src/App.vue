<template>
    <div>

        <h1>Witaj w systemie zapisów na zajecia</h1>

        <div v-if="authenticatedUsername != ''">
            <h3 v-if="authenticatedUsername">Jestes zalogowany jako: {{authenticatedUsername}}</h3>
            <a @click="logMeOut">Wyjdz</a>
        </div>

        <div v-else>
            <login-form @login="logMeIn($event)"></login-form>

        </div>

    </div>
</template>

<script>
    import "milligram";
    import LoginForm from "./LoginForm";
    import MeetingPage from "./meetings/MeetingPage";
    import MeetingsList from "./meetings/MeetingsList";
    import NewMeetingForm from "./meetings/NewMeetingForm";

    export default {
        components: {LoginForm, MeetingPage},
        data() {
            return {
                email: '',
                authenticatedUsername: ''
            };
        },
        methods: {
            logMeIn(userName) {
                this.authenticatedUsername = userName;

            },
            logMeOut() {
                this.authenticatedUsername = ''
            }

        }
    }
</script>

<style>

</style>
