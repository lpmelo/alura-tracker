<template>
  <div class="box">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulário para criação de uma nova tarefa"
      >
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa você deseja
        iniciar?"
          v-model="taskDescription"
        />
      </div>
      <div class="column">
        <TimeDelayer @on-stop-interval="endTask" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TimeDelayer from "./TimeDelayer.vue";

export default defineComponent({
  name: "FormAlura",
  emits: ["onSave"],
  components: { TimeDelayer },
  data() {
    return {
      taskDescription: "",
    };
  },
  methods: {
    endTask(timer: number): void {
      this.$emit("onSave", {
        seconds: timer,
        taskDescription: this.taskDescription,
      });
      this.taskDescription = "";
    },
  },
});
</script>
