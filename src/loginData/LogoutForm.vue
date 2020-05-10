<template>
    <div class="row">
        <h2 class="column">Witaj {{this.$parent.authenticatedUsername}}!</h2>
        <button class="column-70 button button-outline" @click="logout()" >Wyloguj</button>
    </div>
</template>

<script>
    export default {

        data() {
            return {
                authenticatedUsername: '',
            }
        },
        methods: {
            logout() {
                this.$emit('logout', false);
            }
        }
    }
</script>

<style scoped>

</style>