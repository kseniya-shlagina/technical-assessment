<template>
  <div :class="$style.container">
    <Search v-model="searchQuery" />
    <List :cards="filteredData" :search-query="searchQuery" />
  </div>
</template>

<script>
import { go } from 'fuzzysort'
export default {
  props: {
    cards: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      searchQuery: this.$route.query.search || '',
    }
  },
  computed: {
    filteredData() {
      return this.searchQuery === ''
        ? this.cards
        : go(this.searchQuery, this.cards, {
            keys: ['name', 'email', 'title', 'city'],
            allowTypo: true,
            threshold: -10000, // don't return bad results
          }).map((item) => item.obj)
    },
  },
  watch: {
    searchQuery(value) {
      this.$router.push({ path: '/', query: { search: value } })
    },
  },
}
</script>

<style lang="scss" module>
.container {
  width: 680px;
  height: 643px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: 0 auto;
  padding: 19px 12px 0 12px;
  background-color: $color-white;
}
</style>
