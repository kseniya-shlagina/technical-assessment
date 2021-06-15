<template>
  <div :class="$style.container">
    <img src="~/assets/icons/search.svg" alt="Search icon" />
    <input :class="$style.input" :value="value" @input="handleInput" />
  </div>
</template>

<script>
export default {
  model: {
    prop: 'value',
    event: 'change',
  },
  props: {
    value: {
      type: String,
      required: true,
    },
  },
  data: () => ({
    debounce: null,
  }),
  beforeDestroy() {
    clearTimeout(this.debounce)
  },
  methods: {
    handleInput(e) {
      clearTimeout(this.debounce)

      this.debounce = setTimeout(() => {
        this.$emit('change', e.target.value)
      }, 200)
    },
  },
}
</script>
<style lang="scss" module>
.container {
  width: 100%;
  display: flex;
  align-items: center;
  margin-bottom: 20px;
  padding: 12px 19px;
  background-color: $color-light-gray;
  border-radius: 2px;
  box-shadow: 0px 0px 2px rgba(0, 0, 0, 0.12), 0px 2px 2px rgba(0, 0, 0, 0.24);
}

.input {
  width: 100%;
  padding-left: 10px;
  border: none;
  background-color: $color-light-gray;
  font-family: 'Roboto', sans-serif;
  font-size: 24px;

  &:active,
  &:focus {
    outline: none;
  }
}
</style>
