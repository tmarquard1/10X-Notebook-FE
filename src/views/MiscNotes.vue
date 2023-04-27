<template>
    <div class="container">
        <div class="row mt-4">
            <h1>MISC NOTES</h1>
            <input v-model="title" placeholder="Title">
        </div>
    </div>
    <div class="row mt-4">
        <div class="col-md-6">
            <h4>Markdown</h4>
            <textarea v-model="content" class="info"></textarea>
        </div>
        <div class="col-md-6">
            <h4>Formatted Text</h4>
            <div v-html="markdownToHtml" class="info"></div>
        </div>
    </div>
    <button @click="create">Save Note</button>
    <p>{{notesData}}</p>
    <button @click="getNotes">Load Notes</button>
    <div v-for="note in notes" :key="note.id" class="info">
      <h2>Note {{ note.id }}: {{ note.title }}</h2>
        <p></p>
        <h5>{{ note.content }}</h5>
    </div>
</template>


<script>
import {marked} from 'marked';
import axios from 'axios'
export default {
    name: 'misc',
    data() {
        return {
            content: 'Enter Markdown Here...',
            notes: [],
            title: '',
            notesData:{},
            fakeInitialData: {
                id: 1,
                title: 'My First Misc Note',
                content: "This is my first misc note. I'm going to use it to take notes on my first Vue app.",
                tags:[
                    {tag: 'misc'},
                ]
            }
        }
    },
    methods: {
        getNotes() {
            /* axios.get('http://localhost:9000/notes/')
                .then((response) => {
                    console.log(response.data)
                    this.notes = response.data
                })
                .catch((error) => {
                    console.log(error)
                }) */
                console.log(this.fakeInitialData);
                this.notes.push( this.fakeInitialData);
                console.log(this.notes);
        },
        create() {
            const data = {
                // assigne a random id
                id : Math.floor(Math.random() * 100) + 1,
                title: this.title,
                content: this.content,
                tags: [
                    {tag: 'misc'},
                ]
            };
            this.notes.push(data);
            /* axios.post('http://localhost:9000/note/add', data)
                .then(response => {
                    console.log(response);
                })
                .catch(error => {
                    console.log(error);
                }); */
        }
    },
    computed: {
        markdownToHtml() {
        return marked(this.content);
        }
    }

}

</script>

<style scoped>
.container {
    margin-top: 40px;
}
.textarea {
    resize: none;
    border: 2px dashed pink;
    outline: none;
}
.info {
    height: 400px;
    width: 100%;
    background-color: white;
    border: 2px dashed black
    
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

h4 {
    text-align: center;
    
}

button {
  display: block;
  width: 100px;
  margin: 15 px;
}

</style>