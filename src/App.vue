<template>
  <div class="wrapper">
    <Navbar />
    <Notes :notes="notes" />
    <Model 
    @close="isModelShow = false" 
    @addNote="add"
    v-show="isModelShow" 
    :isModelShow="isModelShow" />
    <button class="model-btn" @click="isModelShow = true" v-if="!isModelShow">
      <img src="@/assets/images/edit.svg" alt="edit">
    </button>
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'
import Notes from './components/Notes.vue'
import Model from './components/Model.vue'
export default {
  components: {
    Navbar,
    Notes,
    Model,
  },
  data() {
    return {
      isModelShow: false,
      notes: [
        { id: 1, title: 'Vue', text: 'Lorem Lorem Lorem', date: '07.03.2022' },
        { id: 2, title: 'React', text: 'Lorem Lorem Lorem', date: '07.03.2022' },
        { id: 3, title: 'Php', text: 'Lorem Lorem Lorem', date: '07.03.2022' },
        { id: 3, title: 'Php', text: 'Lorem Lorem Lorem', date: '07.03.2022' },
      ],
    }
  },
  methods: {
    add(note){
      this.notes.push(note)
    }
  },

}
</script>