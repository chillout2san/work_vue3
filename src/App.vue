<template>
  <div>
    <h1>ToDoリスト</h1>
    <label
      ><input
        type="radio"
        name="task"
        @click="display = 'すべて'"
        checked
      />すべて</label
    >
    <label
      ><input
        type="radio"
        name="task"
        @click="display = '作業中'"
      />作業中</label
    >
    <label
      ><input type="radio" name="task" @click="display = '完了'" />完了</label
    >

    <table>
      <thead>
        <tr>
          <th>ID</th>
          <th>コメント</th>
          <th>状態</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(todo, index) in selectedTodos" v-bind:key="index">
          <th>{{ todo.id }}</th>
          <th>{{ todo.task }}</th>
          <th>
            <button @click="changeStatus(todo.id)">{{ todo.status }}</button>
          </th>
          <th><button @click="deleteTask(todo.id)">削除</button></th>
        </tr>
      </tbody>
    </table>
    <h2>新規タスクの追加</h2>
    <input type="text" v-model="task" /><button @click="pushTask">追加</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      id: 0,
      task: '',
      status: '作業中',
      display: 'すべて',
      todos: []
    };
  },
  computed: {
    selectedTodos() {
      const display = this.display;
      if (display === 'すべて') {
        return this.todos;
      } else {
        return this.todos.filter(todo => {
          return todo.status === display;
        });
      }
    }
  },
  methods: {
    pushTask() {
      const todoElm = {
        id: this.id,
        task: this.task,
        status: this.status
      };
      this.todos.push(todoElm);
      this.id += 1;
      this.task = '';
    },
    deleteTask(id) {
      this.todos.splice(id, 1);
      this.id -= 1;
      for (let i = 0; i < this.todos.length; i++) {
        this.todos[i].id = i;
      }
    },
    changeStatus(id) {
      if (this.todos[id].status === '作業中') {
        this.todos[id].status = '完了';
      } else {
        this.todos[id].status = '作業中';
      }
    }
  }
};
</script>

<style></style>
