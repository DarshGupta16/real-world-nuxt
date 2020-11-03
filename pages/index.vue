<template>
  <div>
    <h1>Events</h1>
  </div>
</template>

<script>
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
    $axios.get('http://localhost:3000/events').then((res) => {
      return {
        events: res.data,
      }
    })
  },
}
</script>
