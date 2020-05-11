<template>
        <form @submit.prevent="addNewMeeting()">
            <h3>Dodaj nowe spotkanie</h3>
            <label>Nazwa</label>
            <input type="text" v-model="newMeeting.name">
            <label>Opis</label>
            <textarea v-model="newMeeting.description"></textarea>
            <button>Dodaj</button>
            <span v-if="emptyMeetingName" > Spotkanie nie może być puste</span>
        </form>
</template>

<script>
    export default {
        data() {
            return {
                newMeeting: {meetingUsers: []},
                emptyMeetingName: false
            };
        },
        methods: {
            addNewMeeting() {
                if (this.newMeeting.name){
                    this.$emit('added', this.newMeeting);
                    this.newMeeting = {meetingUsers: []};
                } else {
                    this.emptyMeetingName = true
                }
            }
        }
    }
</script>
<style>
    span{
        color: red;
    }
</style>