<template>
  <div class="wrapper">
    <Navbar />
    <Notes :notes="notes"/>
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'
import Notes from './components/Notes.vue'
export default {
  components: {
    Navbar,
    Notes
  },
  data() {
    return {
      notes: [
        { id: 1, title: 'Vue', text: 'Lorem Lorem Lorem', date: '07.03.2022' },
        { id: 2, title: 'React', text: 'Lorem Lorem Lorem', date: '07.03.2022' },
        { id: 3, title: 'Php', text: 'Lorem Lorem Lorem', date: '07.03.2022' },
        { id: 3, title: 'Php', text: 'Lorem Lorem Lorem', date: '07.03.2022' },
      ]
    }
  }

}
</script>