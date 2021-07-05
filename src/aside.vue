<template>
  <aside>
    <div class="aside-search">
      <input
        v-model="search"
        type="text"
        class="aside-searchText"
        placeholder="поиск заметок..."
        @input="filter"
      />
      <i class="fa fa-search" aria-hidden="true"></i>
    </div>
    <div v-if="search.length" class="aside-searchResult">
      <p class="zeroSearch" v-if="filtred.length === 0">
        По вашему запросу заметок не найдено
      </p>
      <ul class="searchList">
        <li class="searchList-item" v-for="note in filtred" :key="note.title">
          <p>{{ note.title }}</p>
        </li>
      </ul>
    </div>
    <ul class="asideList">
      <li
        @click="correct(idx)"
        class="asideList-item"
        v-for="(note, idx) in notes"
        :key="note.title"
      >
        <p>{{ note.title }}</p>
      </li>
    </ul>
  </aside>
</template>

<script>
export default {
  props: ['notes', 'index', 'isCorrection'],
  data () {
    return {
      search: '',
      filtred: [],
      correction: this.isCorrection
    }
  },
  methods: {
    correct (idx) {
      this.correction = true
      this.$emit('changeIdAside', idx)
    },
    filter () {
      const regexp = new RegExp(this.search, 'i')
      this.filtred = this.notes.filter((note) => regexp.test(note.title))
    }
  }
}
</script>
