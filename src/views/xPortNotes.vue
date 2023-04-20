<template>
  <div class="container">
    <h1>ALL NOTES</h1>
    <button @click="getNotes">Load Notes</button>
    <div v-for="note in notes" :key="note.id" class="info">
      <h2>Note {{ note.id }}: {{ note.title }}</h2>
        <p></p>
        <h5>{{ note.content }}</h5>
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

<style scoped>
.container {
    margin-top: 40px;
}

.info {
    height: 200px;
    width: 100%;
    background-color: white;
    border: 2px black
    
}
h1 {
    color:rgb(16, 163, 200);
    text-align: center;
    margin: 0
}

h3 {
    color: rgb(16, 165, 100);
    text-align: center;
    margin: 0
}

button {
  display: block;
  width: 100px;
  margin: 15 px;
}

</style>