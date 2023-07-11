<template>
  <div class="wrapper">
    <Navbar />
    <Notes :notes="notes" />
    <Model
      @close="isModelShow = false"
      @addNote="add"
      v-show="isModelShow"
      :isModelShow="isModelShow"
    />
    <button class="model-btn" @click="isModelShow = true" v-if="!isModelShow">
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
      notes: [],
    };
  },
  mounted() {
    this.getNotes()
  },
  methods: {
    add(note) {
      this.notes.push(note);
    },
    getNotes(){
      let localNote = localStorage.notes
      console.log(localNote);
      if(localNote){
        this.notes = JSON.parse(localNote)
      }
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