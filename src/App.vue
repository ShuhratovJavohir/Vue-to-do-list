<template>
  <div class="wrapper">
    <Navbar />
    <Notes :notes="notes" @delNotes="delNotes" @change="change" />
    <Model @close="isModelShow = false" @addNote="add" @changeNote="changeNote" v-show="isModelShow"
      :isModelShow="isModelShow" :edit="edit" :editedNote="editedNote" />
    <button class="model-btn" @click="this.isModelShow = true, this.edit = false" v-if="!isModelShow">
      <img src="@/assets/images/edit.svg" alt="edit" />
    </button>
  </div>
</template>

<script>
import Navbar from "./components/Navbar.vue";
import Notes from "./components/Notes.vue";
import Model from "./components/Model.vue";
export default {
  components: {
    Navbar,
    Notes,
    Model,
  },
  data() {
    return {
      isModelShow: false,
      edit: false,
      notes: [],
      editedNote: {},
    };
  },

  mounted() {
    this.getNotes()

  },
  methods: {
    add(note) {
      this.notes.push(note);
    },
    change(id) {
      this.isModelShow = this.edit = true
      let currentNote = this.notes.find(note => note.id == id)
      this.editedNote = currentNote
    },
    changeNote(newNote) {
      this.notes.forEach(note => {
        if (note.id == newNote.id) {
          note.title = newNote.title
          note.text = newNote.text
          note.date = newNote.date
        }
      })
    },
    getNotes() {
      let localNote = localStorage.notes
      if (localNote) {
        this.notes = JSON.parse(localNote)
      }
    },
    delNotes(id) {
      let index = this.notes.findIndex((note) => note.id == id)
      this.notes.splice(index, 1);
    },
  },
  watch: {
    notes: {
      handler() {
        localStorage.notes = JSON.stringify(this.notes);
      },
      deep: true,
    },
  },
};
</script>