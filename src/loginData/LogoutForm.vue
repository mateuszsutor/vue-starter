<template>
    <div>
        <h2 >Witaj {{this.$parent.authenticatedUsername}}!</h2>
        <button @click="logout()" >Wyloguj</button>
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