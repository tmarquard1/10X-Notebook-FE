<template>
    <div class="container">
        <div class="row mt-4">
            <h1>NVIEW NOTES</h1>
        </div>
    </div>
    <div class="row mt-4">
        <div class="col-md-6">
            <h4>Markdown</h4>
            <textarea v-model="markdown" class="info"></textarea>
        </div>
        <div class="col-md-6">
            <h4>Formatted Text</h4>
            <div v-html="markdownToHtml" class="info"></div>
        </div>
    </div>
    <button @click="addNote">Save</button>
</template>

<script>
import {marked} from 'marked';

export default {
name: 'App',
components: {
},
data() {
    return {
    markdown: 'Enter Markdown Here...',
    };
},
computed: {
    markdownToHtml() {
    return marked(this.markdown);
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

h4 {
    text-align: center;
    
}

</style>