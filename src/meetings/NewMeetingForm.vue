<template>
    <div>
        <form @submit.prevent="addNewMeeting()">
            <h3>Dodaj nowe spotkanie</h3>
            <label>Nazwa</label>
            <input type="text" v-model="newMeeting.name">
            <label>Opis</label>
            <textarea v-model="newMeeting.description"></textarea>
            <button @click="isEmpty">Dodaj</button>
            <span v-if="warning">Spotkanie nie może być puste</span>
        </form>

    </div>

</template>

<script>
    export default {
        data() {
            return {
                newMeeting: {meetingUsers: []},
                warning: false
            };
        },
        methods: {
            addNewMeeting() {
                this.$emit('added', this.newMeeting);
                this.newMeeting = {meetingUsers: []};
            },
            //ToDo
            isEmpty(){
                this.warning = true;
            }
        }
    }
</script>
<style>
    span{
        color: red;
    }
</style>