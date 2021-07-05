<template>
  <div class="mainWindow">
    <header-comp
      :isCorrection="correction"
      :is-open="isOpen"
      @action="openEditor"
    ></header-comp>
    <div class="container">
      <aside-bar
        :isCorrection="correction"
        @changeIdAside="changeIDAside"
        :notes="notes"
        :index="id"
      ></aside-bar>

      <notes-window
        :index="id"
        :open="window"
        :notes="notes"
        :is-open="isOpen"
        :titles="title"
        @closeEdit="closeEditor"
        @changeID="change"
      ></notes-window>
    </div>
  </div>
</template>

<script>
import './theme.css'
import editor from './editor'
import header from './header.vue'
import asideBar from './aside.vue'
import notes from './notes.vue'
export default {
  name: 'App',
  components: {
    'edit-block': editor,
    'header-comp': header,
    'aside-bar': asideBar,
    'notes-window': notes
  },

  data () {
    return {
      notes: [
        {
          title: 'Первая заметка',
          text: 'Привет! Это твоя первая заметка'
        }
      ],
      isOpen: false,
      correction: false,
      title: 'Список заметок',
      id: 0
    }
  },

  computed: {
    window () {
      if (this.isOpen === true && this.correction === false) {
        return 'newNote'
      } else if (this.isOpen === false && this.correction === false) {
        return 'desk'
      } else if (this.isOpen === false && this.correction === true) {
        return 'correct'
      }
    }
  },

  methods: {
    changeIDAside (data) {
      this.id = data
      this.correction = true
    },
    change (data) {
      this.id = data
    },
    closeEditor () {
      this.isOpen = false
      this.correction = false
    },
    openEditor () {
      this.isOpen = true
    }
  }
}
</script>

<style lang="scss">
</style>
