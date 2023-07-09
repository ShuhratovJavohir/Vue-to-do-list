<template>
  <div class="wrapper">
    <Navbar/>
    <Notes/>
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'
import Notes from './components/Notes.vue'
  export default {
  components: { Navbar, Notes },
    
  }
</script>