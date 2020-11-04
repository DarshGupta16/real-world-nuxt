<template>
  <div>
    <h1>{{ event.title }}</h1>
  </div>
</template>

<script>
import EventService from '@/services/EventService.js'
export default {
  head() {
    return {
      title: 'Event #' + this.id,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'What you need to know about event #' + this.id,
        },
      ],
    }
  },
  async asyncData({ error, params }) {
    try {
      const { data } = await EventService.getEvent(params.id)
      return {
        event: data,
      }
    } catch (e) {
      error({
        statusCode: 503,
        message: 'Unable to fetch events at this time.. 😟 Please try again.',
      })
    }
  },
}
</script>
