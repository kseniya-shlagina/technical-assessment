<template>
  <div :class="$style.card">
    <img alt="avatar" :src="source.avatar" :class="$style.image" />
    <div :class="$style.innerContainer">
      <div :class="$style.cardHeader">
        <div :class="$style.title">
          <TextHighlight :search-query="searchQuery" :text="source.name">
          </TextHighlight>
        </div>
        <div :class="$style.caption">
          <TextHighlight :search-query="searchQuery" :text="source.email">
          </TextHighlight>
        </div>
      </div>
      <div :class="[$style.subTitle, $style.caption]">
        <TextHighlight
          :search-query="searchQuery"
          :text="source.title"
        ></TextHighlight>
      </div>
      <div :class="$style.caption">
        <TextHighlight
          :search-query="searchQuery"
          :text="source.address + ', ' + source.city"
        ></TextHighlight>
      </div>
      <button :class="$style.button">SKIP SELECTION</button>
    </div>
  </div>
</template>

<script>
import TextHighlight from './TextHighlight'

export default {
  components: {
    TextHighlight,
  },
  props: {
    source: {
      type: Object,
      required: true,
    },
    searchQuery: {
      type: String,
      required: true,
    },
  },
}
</script>

<style lang="scss" module>
.card {
  width: 100%;
  display: flex;
  background-color: $color-light-gray;
  border-radius: 3px;
  box-shadow: 0 0 2px rgba(0, 0, 0, 0.12), 0 2px 2px rgba(0, 0, 0, 0.12);
  margin-bottom: 20px;
}

.innerContainer {
  width: 100%;
  display: flex;
  flex-direction: column;
  padding: 10px 9px 19px 27px;
}

.cardHeader {
  display: flex;
  justify-content: space-between;
}

.title {
  font-size: 24px;
  line-height: 32px;
}

.subTitle {
  font-weight: bold;
}

.caption {
  font-size: 14px;
  line-height: 20px;
  color: rgba(0, 0, 0, 0.543846);
}

.button {
  margin-top: 17px;
  padding-left: 22px;
  background: none;
  border: none;
  font-family: Roboto, sans-serif;
  font-size: 14px;
  font-weight: 500;
  text-align: left;
  color: $color-green;
}

.image {
  min-width: 134px;
  height: 136px;
  border-top-left-radius: 3px;
  border-bottom-left-radius: 3px;
  background-color: rgba(0, 0, 0, 0.25);
  object-fit: cover;
}
</style>
