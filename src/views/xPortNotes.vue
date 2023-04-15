<template>
  <div class="container">
    <div class="row mt-4">
      <h1>ALL NOTES</h1>
    </div>
  </div>
  <div class="row mt-4">
    <div class="col-md-6">
      <button @click="getNotes">Load Notes</button>
      <div v-for="note in notes" :key="note.id">
        <h5>{{ note.id }}. {{ note.title }}. {{ note.tags }}. {{ note.content }}</h5>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'xPort',
  data() {
    return {
      notes: [],
    }
  },
  methods: {
    getNotes() {
      axios.get('http://localhost:9000/notes/')
        .then((response) => {
          console.log(response.data)
          this.notes = response.data
        })
        .catch((error) => {
          console.log(error)
        })
    },
  },
}
</script>
