<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <SideBar />
    </div>

    <div class="column is-three-quarter">
      <FormAlura @onSave="saveNewTask" />
      <div class="lista">
        <CardTask v-for="(task, index) in allTasks" :key="index" :task="task" />
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import SideBar from "./components/SideBar.vue";
import FormAlura from "./components/FormAlura.vue";
import CardTask from "./components/CardTask.vue";
import ITasks from "./interfaces/ITasks";

export default defineComponent({
  name: "App",
  components: {
    SideBar,
    FormAlura,
    CardTask,
  },
  data() {
    return {
      allTasks: [] as ITasks[],
    };
  },
  methods: {
    saveNewTask(task: ITasks) {
      this.allTasks.push(task);
    },
  },
});
</script>

<style>
.lista {
  padding: 1.25rem;
}
</style>
