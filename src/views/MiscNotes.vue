<template>
    <div>
      <input v-model="title" placeholder="Title">
      <input v-model="content" placeholder="Content">
      <button @click="create">Save Note</button>
      <p>{{notesData}}</p>
    </div>
  </template>
  
  <script lang="ts">
  import axios from 'axios';
  export default {
    data() {
      return {
        title: '',
        content: '',
        notesData: { }
      };
    },
    mounted() {
      axios
        .get('http://localhost:9000/notes/')
        .then((response) => {
          console.log(response);
          this.notesData=response;
        })
    },
    methods: {
      create() {
        const data = {
          title: this.title,
          content: this.content
        };
        axios.post('http://localhost:9000/note/add', data)
          .then(response => {
            console.log(response);
          })
          .catch(error => {
            console.log(error);
          });
      }
    }
  }
</script>