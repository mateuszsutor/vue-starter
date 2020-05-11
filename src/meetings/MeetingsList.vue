<template>
    <div>
        <div v-if="meetings.length > 0">
            <h3>Zaplanowane zajęcia ({{ meetings.length }})</h3>
            <table>
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
                    <td>
                        <ul>
                            <li v-for="user in meeting.meetingUsers" :key="user">
                                {{user}}
                            </li>
                        </ul>
                    </td>

                    <td class="button-controller">
                        <button class="button button-outline"
                                @click="registerToMeeting(meeting)"
                                v-if="meeting.meetingUsers.indexOf(user) < 0 ">Zapisz się</button>

                        <button class="button button-outline"
                                @click="leaveMeeting(meeting)"
                                v-else>Wypisz się</button>

                        <button class="button"
                                id="button-delete"
                                @click="deleteEmptyMeeting(meeting)"
                                v-if="meeting.meetingUsers.length === 0">Usuń puste spotkanie</button>
                    </td>
                </tr>
                </tbody>
            </table>
        </div>
        <div v-else>
            <p>Brak zaplanowanych spotkań</p>
        </div>
    </div>



</template>

<script>
    export default {
        props: ['meetings', 'user'],

        methods: {
            leaveMeeting(meeting) {
                this.$emit('leave', meeting)
            },

            registerToMeeting(meeting) {
                this.$emit('register', meeting)
            },

            deleteEmptyMeeting(meeting) {
                this.$emit('delete', meeting)
            }
        }
    }
</script>

<style>
    .button-controller {
        text-align: right;
    }
    #button-delete {
        margin-left: 5px;
    }
</style>
