<template>
  <Transition name="model">
    <div class="model" @click="closeModel">
      <div class="model__content" @click.stop>
        <h2 class="model-title">Добавить заметку</h2>
        <div class="model__inputs">
          <div class="model__inputs_input">
            <p class="model__inputs_input-title">Title</p>
            <input v-model="title" class="model__inputs_input-input" type="text" placeholder="Tile">
          </div>
          <div class="model__inputs_input">
            <p class="model__inputs_input-title">Content</p>
            <textarea v-model="text" class="model__inputs_input-input" type="text" placeholder="Content"></textarea>
          </div>
        </div>
        <div class="model__btns">
          <button @click="closeModel" class="model__btns-btn cancel">Отменить</button>
          <button @click="addNote" class="model__btns-btn add">Добавить</button>
        </div>
      </div>
    </div>
  </Transition>
</template>

<script>
export default {
  props: {
    isModelShow: {
      typeof: Boolean,
    }
  },
  data() {
    return {
      title: '',
      text: '', 
      
    }
  },
  methods: {
    closeModel() {
      this.$emit('close')
      this.title = this.text = '';
    },
    addNote() {
      if (this.title != '' && this.text != '') {
        const note = {
          title: this.title,
          text: this.text,
          data: new Date().toLocaleDateString()
        }
        this.$emit('addNote', note)
        this.closeModel()
      } else {
        
      }
    }
  },

}
</script>