<template>
  <div class="heck">Quotes From the Stream!
    <div class="quote-text">
      <li v-for="item in text" :key="item">
        {{ item }}
      </li>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, onMounted, ref } from 'vue';
export default defineComponent({
  name: "QuoteViewer",
  async setup() {
    const text = ref(["Loading..."]);
    async function getQuotes() {
      // Axios?
      const response = await fetch('https://feathers.exposed/api/quotes');
      const jsonResponse = await response.json();
      return (jsonResponse as Array<any>).map(e => { return `#${e.ID}: "${e.Quote}" -- ${e.GameName}` });
    }
    onMounted(async () => {
      text.value = await getQuotes();
    });
    return {
      text
    }
  }
});
</script>

<style>
.heck {
  background-color: #c0230e;
  border-radius: 2mm;
  padding: 10px;
}

.quote-text {
  font-size: medium;
}
</style>