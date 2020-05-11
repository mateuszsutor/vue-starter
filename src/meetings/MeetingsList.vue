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
            <td>{{meeting.meetingsUsers}}</td>
            <td>
                <button class="button button-outline"
                        @click="registerToMeeting(meeting)">Zapisz się</button>


                <button class="button button-outline">Wypisz się</button>


                <button class="button">Usuń puste spotkanie</button>
            </td>
        </tr>
        </tbody>
    </table>
</template>

<script>
    export default {
        props: ['meetings', 'user'],

        methods: {
            leaveMeeting(){
            },

            registerToMeeting(meeting){
                this.$emit('register', meeting)
            },

            deleteEmptyMeeting(){

            }
        }
    }
</script>