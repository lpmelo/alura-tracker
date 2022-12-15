<template>
  <div class="box has-text-weight-bold">
    <div class="columns">
      <div class="column is-7">{{ task.taskDescription }}</div>
      <div class="column">
        <TimeCounter :timer="task.seconds" />
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent, PropType } from "vue";
import TimeCounter from "./TimeCounter.vue";
import ITasks from "../interfaces/ITasks";

export default defineComponent({
  name: "CardTask",
  components: {
    TimeCounter,
  },

  props: {
    task: {
      type: Object as PropType<ITasks>,
      required: true,
    },
  },
});
</script>

<style scoped>
.box {
  background: #faf0ca;
}
</style>
