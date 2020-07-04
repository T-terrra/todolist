<template>
  <div>
    <div>
      <b>ToDoList</b>
    </div>
    <div>
      <label>
        タスク
        <input class="taskInput" type="text" v-model="newTaskName" />
      </label>
      <label>
        期限
        <input class="untilInput" type="text" v-model="newTaskUntil" />
      </label>
      <button @click="addTask">add</button>
    </div>
    <div>
      <div v-for="task in items" :key="task.finished">
        <div class="task">
          <span class="taskName">タスク:{{ task.taskName }}</span>
          <span class="until">{{ task.until }}まで</span>
          <span v-if="task.finished == 0">
            <button class="finish" @click="task.finished += 1">完了</button>
          </span>
          <span v-if="task.finished == 1">
            <span class="finish">完了済み</span>
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ToDoList",
  data() {
    return {
      items: [{ taskName: "タスク1", until: "終わる", finished: 1 }],
      newTaskName: "",
      newTaskUntil: ""
    };
  },
  methods: {
    addTask() {
      this.items.push({
        taskName: this.newTaskName,
        until: this.newTaskUntil,
        finished: 0
      });
      this.newTaskName = "",
      this.newTaskUntil = ""
    }
  }
};
</script>

<style>
.taskName {
  margin-right: 50px;
}
.finish {
  margin-left: 50px;
}
</style>
