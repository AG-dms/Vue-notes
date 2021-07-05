<template>
  <header>
    <div class="header-left">
      <button class="btn" :disabled="curentOpen" @click="openEditor">+</button>
      <h3 class="header-addNote">Добавить заметку</h3>
    </div>
  </header>
</template>

<script>
export default {
  props: ['isOpen', 'isCorrection'],
  data () {
    return {
      isEditOpen: this.isOpen
    }
  },

  computed: {
    curentOpen () {
      if (this.isOpen === true || this.isCorrection === true) {
        return true
      } else {
        return false
      }
    }
  },

  methods: {
    openEditor () {
      this.isEditOpen = true
      this.$emit('action')
    }
  }
}
</script>
