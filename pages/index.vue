<template>
  <div>
    <h1>Events</h1>
    <EventCard
      v-for="(event, index) in events"
      :key="index"
      :event="event"
      :data-index="index"
    />
  </div>
</template>

<script>
import EventCard from '@/components/EventCard.vue'

export default {
  head() {
    return {
      title: 'Event Listing',
      hid: 'description',
      name: 'description',
      content:
        'Where you can find all the events taking place in your neighbourhood',
    }
  },
  asyncData({ $axios }) {
    return $axios.get('http://localhost:3000/events').then((res) => {
      return {
        events: res.data,
      }
    })
  },
  components: {
    EventCard,
  },
}
</script>
