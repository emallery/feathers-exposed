<template>
    <div class="heck">Quotes From the Stream!
        <div class="quote-text">
            {{ getQuotes() }}
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    name: "QuoteViewer",
    methods: {
        async getQuotes() {
            const response = await fetch('https://feathers.exposed/api/quotes');
            return response.json();
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