<template>
    <div class="container">
        <div class="row mt-4">
            <h1>XPORT NOTES</h1>
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
    <input v-model="additional_tags" placeholder="Tags">
    <button @click="create">Save Note</button>
    <p>{{notesData}}</p>
    <button @click="getNotes">Load Notes</button>
    <div v-for="note in notes" :key="note.id" class="info">
      <h2>Note {{ note.id }}: {{ note.title }}</h2>
        <p></p>
        <h5>{{ note.content }}</h5>
        <h6>{{ note.tags }}</h6>
    </div>
</template>


<script>
import {marked} from 'marked';
import axios from 'axios'
export default {
    name: 'xport',
    data() {
        return {
            content: 'Enter Markdown Here...',
            notes: [],
            title: '',
            notesData:{},
            fakeInitialData: {
                id: 1,
                title: 'My First nPort Note',
                content: "This is my first nPort note. I'm going to use it to take notes on my first Vue app.",
                tags:[
                    {tag: 'nport'},
                ]
            },
            fakeInitialListofData:  // When the filter works, make this more challenging by having multiple tags per note. Including BOTH a nview and nport tag on one note. case sensitive
            [
                {
                    id: 1,
                    title: 'My First nPort Note',
                    content: "This is my first nPort note. I'm going to use it to take notes on my first Vue app.",
                    tags:[
                        {tag: 'nport'},
                        {tag: 'xport'}
                    ]
                },
                {
                    id: 2,
                    title: 'My First nVuew Note and Second nPort',
                    content: "This is my first nview note. I'm going to use it to take notes on my first Vue app.",
                    tags:[
                        {tag: 'nview'},
                        {tag: 'nport'}
                    ]
                },
                {
                    id: 3,
                    title: 'My Secnd nVuew Note',
                    content: "This is my Second nview note. I'm going to use it to take notes on my first Vue app.",
                    tags:[
                        {tag: 'nview'},
                    ]
                },
                {
                    id: 4,
                    title: 'My Third nPort Note',
                    content: "This is my Secind nPort note. I'm going to use it to take notes on my first Vue app.",
                    tags:[
                        {tag: 'nport'},
                    ]
                },
            ]
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

                // Use fake initial list of data 
                // The fake initial list of data needs to be filtered for the nport tag. 
                // Then the filtered LIST needs to be applied to this.notes so that it is rendered on the screen 

                // as part of this, fix the bug where data is loaded on top of old data. (unique data rendered)
                //console.log(this.fakeInitialData);
                //if(orig data)
               
                //this.notes.push(this.fakeInitialData);
                this.notes = this.filteredNotes;
                console.log(this.notes);
        },
        create() {
            const data = {
                // assigne a random id
                id : Math.floor(Math.random() * 100) + 1,
                title: this.title,
                content: this.content,
                tags: [
                    {tag: 'xport'},
                    {tag: this.additional_tags}
                ]
            };
            this.notes.push(data);
            this.title = "";
            this.content = "";
            this.additional_tags ="";
        }
    },
    computed: {
        markdownToHtml() {
            return marked(this.content);
        },
        filteredNotes(){
            return this.fakeInitialListofData.filter((note) => note.tags.some((tag) => tag.tag === 'xport')
            );
        },
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
ul {
  list-style: none;
  display: flex;
  align-items: center;
  gap: 7px;
  margin: 0;
  padding: 0;
}
.tag {
  background: rgb(250, 104, 104);
  padding: 5px;
  border-radius: 4px;
  color: white;
  white-space: nowrap;
}


</style>