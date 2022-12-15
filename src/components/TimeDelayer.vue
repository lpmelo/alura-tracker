<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <TimeCounter :timer="timer" />
    <button class="button" @click="startCount" :disabled="onInterval">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="button" @click="endCount" :disabled="!onInterval">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TimeCounter from "./TimeCounter.vue";

export default defineComponent({
  name: "TimeDelayer",
  emits: ["onStopInterval"],
  components: {
    TimeCounter,
  },
  data() {
    return {
      timer: 0,
      timerRef: 0,
      onInterval: false,
    };
  },
  methods: {
    startCount() {
      this.onInterval = true;
      this.timerRef = setInterval(() => {
        this.timer += 1;
      }, 1000);
    },
    endCount() {
      this.onInterval = false;
      clearInterval(this.timerRef);
      this.$emit("onStopInterval", this.timer);
      this.timer = 0;
    },
  },
});
</script>
