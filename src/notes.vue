<template>
  <div class="note-window">
    <!-- <component
      :notes="notes"
      :is="componentName"
      @addId="showId"
      :idx="id"
    ></component> -->
    <edit-block v-if="this.open === 'newNote'" :notes="notes"></edit-block>
    <correct-note
      :notes="notes"
      :index="id"
      v-if="this.open === 'correct'"
    ></correct-note>
    <note-desk
      @correction="correctNote"
      v-if="this.open === 'desk'"
      :notes="notes"
      :index="id"
    ></note-desk>
  </div>
</template>

<script>
import editor from './editor.vue'
import cardNote from './cardNote.vue'
import noteDesk from './noteDesk.vue'
import correctNote from './correctNote.vue'

export default {
  emits: ['changeID', 'closeEdit'],
  props: ['titles', 'isOpen', 'notes', 'open', 'correction', 'index'],
  components: {
    correctNote,
    'card-note': cardNote,
    'edit-block': editor,
    noteDesk
  },
  computed: {
    id () {
      return this.index
    }
  },
  data () {
    return {}
  },
  methods: {
    correctNote (data) {
      this.$parent.correction = true
      // this.id = data;
      this.$emit('changeID', data)
    }
  }
}
</script>

<style>
</style>
