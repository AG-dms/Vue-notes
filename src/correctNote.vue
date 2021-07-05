<template>
  <div class="editor-bar">
    <div class="editor-bar-left" @click="closeEditor">
      <span class="editor-bar-closeIcon">&#10148;</span>
      <span class="editor-bar-close">Назад</span>
    </div>
    <div class="editor-bar-right" @click="saveNote">
      <span class="editor-bar-save">Сохранить</span>
      <span class="editor-bar-saveIcon">&#10004;</span>
    </div>
  </div>
  <div @keypress.enter="saveNote">
    <div class="editor">
      <input
        class="editor-title"
        type="text"
        name=""
        placeholder="Заголовок..."
        v-model="noteTitle"
      />
    </div>
    <textarea
      class="editor-text"
      placeholder="Текст заметки"
      v-model="noteText"
    ></textarea>
  </div>
</template>

<script>
export default {
  props: ['notes', 'index'],
  computed: {
    text () {
      return 'text'
    }
  },
  data () {
    return {
      noteTitle: this.notes[this.index].title,
      noteText: this.notes[this.index].text
    }
  },
  methods: {
    saveNote () {
      this.notes[this.index].title = this.noteTitle
      this.notes[this.index].text = this.noteText
      this.$parent.$emit('closeEdit')
    },
    closeEditor () {
      this.$parent.$emit('closeEdit')
    }
  }
}
</script>

<style>
</style>
