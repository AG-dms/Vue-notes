<template>
  <li class="list-item" v-for="(item, idx) in notes" v-bind:key="item.title">
    <div class="card" @click="correct(idx)">
      <h3 class="card-title">{{ item.title }}</h3>
      <p class="card-text">{{ item.text }}</p>
      <button @click.stop="remove(idx)" class="btn close">&times;</button>
    </div>
  </li>
</template>

<script>
export default {
  emits: ['correctNote'],
  props: ['notes', 'isOpen', 'index'],
  data () {
    return {}
  },
  methods: {
    correct (idx) {
      this.$parent.$emit('correction', idx)
    },
    remove (idx) {
      this.notes.splice(idx, 1)
    }
  }
}
</script>

<style>
</style>
