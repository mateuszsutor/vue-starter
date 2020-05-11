<template>
    <table v-if="meetings.length > 0">
        <thead>
        <tr>
            <th>Nazwa spotkania</th>
            <th>Opis</th>
            <th>Użytkownik</th>
            <th></th>
            
        </tr>
        </thead>
        <tbody>
        <tr v-for="meeting in meetings" :key="meeting.name">
            <td>{{ meeting.name }}</td>
            <td>{{ meeting.description }}</td>
            <td>{{meeting.meetingUsers}}</td>
            <td>
                <button class="button button-outline"
                        @click="registerToMeeting(meeting)">Zapisz się</button>


                <button class="button button-outline"
                        @click="leaveMeeting(meeting)">Wypisz się</button>


                <button class="button"
                        @click="deleteEmptyMeeting(meeting)">Usuń puste spotkanie</button>
            </td>
        </tr>
        </tbody>
    </table>
</template>

<script>
    export default {
        props: ['meetings', 'user'],

        methods: {
            leaveMeeting(meeting){
                this.$emit('leave', meeting)
            },

            registerToMeeting(meeting){
                this.$emit('register', meeting)
            },

            deleteEmptyMeeting(meeting){
                this.$emit('delete', meeting)
            }
        }
    }
</script>