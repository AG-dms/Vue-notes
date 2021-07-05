<template>
  <div class="note-desck">
    <div class="note-desckTitle">
      <h1>Список заметок</h1>
    </div>
    <p v-if="!notes.length">Список заметок пуст</p>
    <ul class="list" v-if="notes.length">
      <card-note :notes="notes"></card-note>
    </ul>
  </div>
</template>

<script>
import cardNote from './cardNote.vue'
export default {
  props: ['notes', 'index'],
  components: {
    'card-note': cardNote
  }
}
</script>

<style>
</style>
