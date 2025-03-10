<template>
  <p>This text is not in Dutch, Google. Please stop asking to translate it!</p>
  <img src="./assets/feathers-exposed-1080.webp" class="bg-image" />
  <div class="heck">
    <h3>Clicky Stuff!</h3>
    <nav>
      <a href="https://twitch.tv/featherderg" title="The place to watch the stream!" target="_blank"
        rel="noopener noreferrer">Twitch</a> |
      <a href="https://bsky.app/profile/featherderg.net" title="On to bluer skies, I guess..." target="_blank"
        rel="noopener noreferrer">Bluesky</a> |
      <a href="https://www.youtube.com/@FeatheryFiddler" title="Weird humansona, nerd!" target="_blank"
        rel="noopener noreferrer">YouTube</a>
    </nav>
    <h6><small>(don't worry, they'll open in a new tab)</small></h6>
  </div>
  <Suspense>
    <QuoteViewer />
    <template #fallback>Loading...</template>
  </Suspense>
  <div class="bottom">
    <div class="button-box">
      <p>Noot n{{ "o".repeat(count) }}t!</p>
      <button @click="count++">Noot</button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import QuoteViewer from "@/components/QuoteViewer.vue";

export default defineComponent({
  name: 'App',
  components: {
    QuoteViewer,
  },
  setup() {
    const count = ref(2);
    return {
      count
    }
  },
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  font-weight: bold;
  font-size: larger;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #0e1a23;
}

html {
  background-color: #1d1d24
}

button {
  box-shadow: 5px 5px 5px -4px rgba(0, 0, 0, 0.52);
}

.bg-image {
  width: 100%;
}

.bottom {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.button-box {
  position: sticky;
  bottom: 5mm;
  background-color: #c0230e;
  border-radius: 2mm;
  padding: 10px;
  margin: 10px;
}

a {
  text-decoration: none;
  transition: 0.4s;
  color: rgb(95, 25, 175);
  filter: drop-shadow(5px 5px 10px #00000070);
}

@media (hover: hover) {
  a:hover {
    color: rgb(245, 221, 243);
  }
}
</style>
