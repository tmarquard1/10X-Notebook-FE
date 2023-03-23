<template>
    <div>
      <input v-model="title" placeholder="Title">
      <input v-model="content" placeholder="Content">
      <button @click="create">Save Note</button>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  export default {
    data() {
      return {
        title: '',
        content: ''
      };
    },
    methods: {
      create() {
        const data = {
          title: this.title,
          content: this.content
        };
        
        axios.post('https://tiffanyclark225-miniature-goldfish-wjjprqq7gjq37pw-9000.preview.app.github.dev/note/add', data)
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
  
  
  
  
  