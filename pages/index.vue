<template>
  <h1>Hi! You are the visitor number {{visitors}}!</h1>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'IndexPage',

  async asyncData({ app }) {

    const url = process.env.BACKEND_API + "/counter";
    const data = await fetch(url, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
    })
    const { count } = await data.json()
    return { visitors: count }
  },

  data() {
    return {
      visitors: 0
    }
  }
})
</script>
