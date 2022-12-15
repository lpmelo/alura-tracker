<template>
  <section>
    <strong>{{ timerPassed }}</strong>
  </section>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "TimeCounter",
  props: {
    timer: {
      type: Number,
      default: 0,
    },
  },
  computed: {
    timerPassed(): string {
      return new Date(this.timer * 1000).toISOString().substr(11, 8);
    },
  },
});
</script>
