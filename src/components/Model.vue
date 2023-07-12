<template>
  <Transition name="model">
    <div class="model" @click="closeModel">
      <div class="model__content" @click.stop>
        <h2 class="model-title">{{ edit ? 'Изменить заметку' : 'Добавить заметку' }}</h2>
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
          
          <button v-show="!edit" @click="addNote" class="model__btns-btn add">Добавить</button>
          <button v-show="edit" @click="editNote" class="model__btns-btn add">Изменить</button>
          
        </div>
      </div>
    </div>
  </Transition>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';

export default {
  props: {
    isModelShow: {typeof: Boolean},
    edit: {typeof: Boolean},
    editedNote: {typeof: Object}
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
    editNote(){
      if(this.title.length > 2 && this.text.length > 2){
        const newEditedNote = {
          id: this.editedNote.id,
          title: this.title,
          text: this.text,
          date: new Date().toLocaleDateString()
        }
        this.$emit('changeNote', newEditedNote)
        this.closeModel()
      }
    },
    addNote() {
      if (this.title != '' && this.text != '') {
        const note = {
          id: uuidv4(),
          title: this.title,
          text: this.text,
          date: new Date().toLocaleDateString()
        }
        this.$emit('addNote', note)
        this.closeModel()
      }
    }
  },

}
</script>