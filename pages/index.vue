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
  async asyncData({ $axios, error }) {
    try {
      const { data } = await $axios.get('http://localhost:3000/events')
      return {
        events: data,
      }
    } catch (e) {
      error({
        statusCode: 503,
        message: 'Unable to fetch events at this time.. 😟 Please try again.',
      })
    }
  },
  components: {
    EventCard,
  },
}
</script>
