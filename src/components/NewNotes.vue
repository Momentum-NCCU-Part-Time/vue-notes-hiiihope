<script setup>
import { ref } from "vue";
import NoteList from "./NoteList.vue";
const newNoteTitle = ref("");
const newNoteBody = ref("");

// fetch request post + Get will go here, linked via import from vue 
const createNote = () => {
  fetch("http://localhost:3000/notes/", {
    method: "POST",
    headers: {"Content-Type": "application/json"},
    body:JSON.stringify({ title: newNoteTitle.value, body: newNoteBody.value }),
    // removed updatedat/ part of stringify Per Chuck, readme value not necessary
  })
  .then((res) => res.json())
  .then((data) => console.log(data));
  resetNote()
};

function getNotes() {
fetch("http://localhost:3000/notes/", {
    method: "GET",
    headers: { "Content-Type": "application/json" },
})
.then((res) => res.json())
.then((data) => (notes.value = data));
};

</script>
