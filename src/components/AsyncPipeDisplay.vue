<template>
<p>
  This is the current value of the stream,
  increasing every {{ (rate || 1000)/1000 }} seconds,
  according to the async pipe:
  <br />
  <span>{{ result }}</span>
</p>
</template>

<script lang="ts">
import { interval } from 'rxjs';
import { defineComponent } from 'vue'
import { asyncPipe } from '@dot-subscribe/vue3-async-pipe';

export default defineComponent({
  name: 'AsyncPipeDisplay',
  props: {
    rate: {
      type: Number,
      required: false
    },
  },
  setup: (props) => {
    const stream = interval(props.rate || 1000);
    const result = asyncPipe(stream);

    return {
      result,
    };
  },
})
</script>

<style scoped>
span {
  font-weight: 700;
}
</style>
