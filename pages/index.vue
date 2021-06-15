<template>
  <SearchBlock :cards="cardsData" />
</template>

<script>
export default {
  async asyncData() {
    const url =
      'https://gist.githubusercontent.com/allaud/093aa499998b7843bb10b44ea6ea02dc/raw/c400744999bf4b308f67807729a6635ced0c8644/users.json'

    const cardsData = await fetch(url).then((res) => res.json())

    return {
      cardsData: cardsData.map((card, idx) => ({ ...card, id: idx })),
    }
  },
}
</script>
