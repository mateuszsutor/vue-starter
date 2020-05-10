<template>
    <div>
        <div v-if="meetings.length === 0">
            <button @click="addNewMeeting">Dodaj nowe spotkanie</button>
            <p>Brak zaplanowanych spotkań</p>
        </div>
        <div v-else>
            <new-meeting-form @added="addNewMeeting($event)"></new-meeting-form>
            <meetings-list :meetings="meetings"></meetings-list>
        </div>
    </div>
</template>

<script>
    import NewMeetingForm from "./NewMeetingForm";
    import MeetingsList from "./MeetingsList";

    export default {
        components: {NewMeetingForm, MeetingsList},
        data() {
            return {
                meetings: []
            };
        },
        methods: {
            addNewMeeting(meeting) {
                this.meetings.push(meeting);
            }
        }
    }
</script>

<style>
    .button {
        margin: 10px;
    }
</style>