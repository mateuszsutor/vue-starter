<template>
    <div>
        <new-meeting-form v-if="showOption" @added="addNewMeeting($event)"></new-meeting-form>

        <button v-else class="button" @click="showMeetingForm">Dodaj nowe spotkanie</button>

        <meetings-list :meetings="meetings" :user="username"
                       @register="addUserToMeeting($event)"
                       @leave="removeUserFromMeeting($event)"
                       @delete="deleteEmptyMeeting($event)"></meetings-list>
    </div>
</template>

<script>
    import NewMeetingForm from "./NewMeetingForm";
    import MeetingsList from "./MeetingsList";

    export default {
        components: {NewMeetingForm, MeetingsList},
        props: ['username'],

        data() {
            return {
                meetings: [],
                showOption: false,
            };
        },
        methods: {
            addNewMeeting(meeting) {
                this.meetings.push(meeting);
                this.showOption = false;
            },

            addUserToMeeting(meeting) {
                meeting.meetingUsers.push(this.username);
            },

            removeUserFromMeeting(meeting) {
                meeting.meetingUsers.splice(meeting.meetingUsers.indexOf(this.username), 1);
            },

            deleteEmptyMeeting(meeting) {
                this.meetings.splice(this.meetings.indexOf(meeting), 1);
            },

            showMeetingForm() {
                this.showOption = true;
            }
        }
    }
</script>
<style>
    .button {
        margin-left: 10px;
        margin-right: 10px;
    }
</style>



