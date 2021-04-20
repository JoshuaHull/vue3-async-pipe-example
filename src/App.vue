<template>
<button @click="showDisplay=!showDisplay">
  <span v-if="showDisplay">Stop</span>
  <span v-else>Start</span>
</button>
<AsyncPipeDisplay v-if="showDisplay" />
<AsyncPipeDisplay  v-if="showDisplay" :rate="2000" />
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import AsyncPipeDisplay from './components/AsyncPipeDisplay.vue'

export default defineComponent({
  name: 'App',
  components: {
    AsyncPipeDisplay
  },
  setup() {
    const showDisplay = ref(false);

    return {
      showDisplay,
    };
  },
})
</script>

<style>
body {
  margin-left: 5rem;
  margin-right: 5rem;
  margin-top: 5rem;
}
</style>
