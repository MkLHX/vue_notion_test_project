<template>
  <div class="hello">
    {{ msg }}
    <NotionRenderer v-if="blockMap" :blockMap="blockMap" />
    <a :href="notionSource" target="_blank">rendered from public notion source</a>
  </div>
</template>

<script>
import { NotionRenderer, getPageBlocks } from "vue-notion";

export default {
  name: "HelloWorld",
  components: {
    NotionRenderer,
  },
  props: {
    msg: String,
  },
  data: () => {
    return {
      blockMap: null,
      notionSource: "https://vanilla-sheep-9ce.notion.site/Quick-Note-bc68fc9d2a804cda892ab8497c254183",
    };
  },
  async created() {
    this.blockMap = await getPageBlocks("bc68fc9d2a804cda892ab8497c254183");
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import "vue-notion/src/styles.css"; /* optional Notion-like styles */

h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
