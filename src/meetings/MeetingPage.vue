<template>
    <div>
        <div v-if="meetings.length === 0">
            <button @click="addNewMeeting">Dodaj nowe spotkanie</button>
            <p>Brak zaplanowanych spotkań</p>
        </div>
        <div v-else>
            <new-meeting-form @added="addNewMeeting($event)"></new-meeting-form>
            <meetings-list :meetings="meetings" :user="username"
                            @register="addUserToMeeting($event)"
                            @leave="removeUserFromMeeting($event)"
                            @delete="deleteEmptyMeeting($event)">
            </meetings-list>
        </div>
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
                meetings: []
            };
        },
        methods: {
            addNewMeeting(meeting) {
                this.meetings.push(meeting);
            },

            addUserToMeeting(meeting){
                meeting.meetingUsers.push(this.username)
            },

            removeUserFromMeeting(meeting) {
                meeting.meetingUsers.splice(meeting.meetingUsers.indexOf(this.username), 1);
            },

            deleteEmptyMeeting(meeting) {
                this.meetings.splice(this.meetings.indexOf(meeting), 1);
            }

        }
    }
</script>

<style>
    .button {
        margin: 10px;
    }
</style>