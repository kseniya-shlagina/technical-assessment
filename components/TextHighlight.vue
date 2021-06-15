<script>
import fuzzysort from 'fuzzysort'

export default {
  props: {
    text: {
      type: String,
      required: true,
    },
    searchQuery: {
      type: String,
      required: true,
    },
  },
  render() {
    const result = fuzzysort.highlight(
      fuzzysort.single(this.searchQuery, this.text),
      '<>',
      '<>'
    )
    if (!result) return <span>{this.text}</span>
    return (
      <span>
        {result.split('<>').map((chunk, index) => (
          <span class={index % 2 === 1 ? 'textHighlight' : ''}>{chunk}</span>
        ))}
      </span>
    )
  },
}
</script>

<style scoped>
.textHighlight {
  background: #fff73b;
}
</style>
