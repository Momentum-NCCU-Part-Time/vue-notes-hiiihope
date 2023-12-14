<script setup>
import { ref } from 'vue';
import NewNotes from './NewNotes.vue';
import NoteEdits from './NoteEdits.vue';
const notes = ref ([])


fetch("http://localhost:3000/notes/", {
    method: "GET",
    headers: { "Content-Type": "application/json" },
})
.then((res) => res.json())
.then((data) => (notes.value = data));

function getNotes() {
fetch("http://localhost:3000/notes/", {
    method: "GET",
    headers: { "Content-Type": "application/json" },
})
.then((res) => res.json())
.then((data) => (notes.value = data));
};

</script>

<template> 
    <div id="notesApp">
    <h1 class="vueNotes">Vue Notes here</h1>
      <NewNote @noteCreated="addNote"/>
      <div id="noteCards">
        
        <div class="noteCard" v-for="note in notes" :key="note.id">
          <h3>{{ note.title }}</h3>
          <br />
          {{ note.body }}
                  </div>
    </div>
      </div>
      </template>
