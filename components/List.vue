<template>
  <div :class="$style.container">
    <VirtualList
      :class="$style.list"
      data-key="id"
      :data-sources="cards"
      :data-component="itemComponent"
      :extra-props="{ searchQuery }"
    />
    <h2 v-if="cards.length === 0" :class="$style.notice">No matches found</h2>
  </div>
</template>

<script>
import VirtualList from 'vue-virtual-scroll-list'
import Card from './Card'

export default {
  components: {
    VirtualList,
  },
  props: {
    cards: { type: Array, required: true },
    searchQuery: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      itemComponent: Card,
    }
  },
}
</script>

<style lang="scss" module>
.container {
  position: relative;
  width: 100%;
}

.list {
  width: 100%;
  height: 550px;
  display: flex;
  flex-direction: column;
  overflow-y: auto;
}

.notice {
  position: absolute;
  top: 0;
  left: 0;
}
</style>
