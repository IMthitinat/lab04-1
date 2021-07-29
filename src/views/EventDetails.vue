<template>
    <div v-if="event">
        <h1>{{ event.title }}</h1>
        <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
        <p>{{ event.description }}</p>
    </div>
</template>

<script>
import EventService from '@/services/EventService.js'
export default {
    props: ['id'],
    data() {
        return {
            event: null,
            

        }
    },
    created() {
        // featch event (by id) and set local event data
        EventService.getEvent(this.id)
        .than(response => {
            this.event = response.data
        })
        .catch(error => {
            console.log(error)
        })
    }
}
</script>
