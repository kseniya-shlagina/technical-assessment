<template>
  <VirtualList
    :class="$style.list"
    :data-key="'id'"
    :data-sources="cards"
    :data-component="itemComponent"
    :extra-props="{ searchQuery }"
  />
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
.list {
  width: 100%;
  height: 550px;
  display: flex;
  flex-direction: column;
  overflow-y: auto;
}
</style>
