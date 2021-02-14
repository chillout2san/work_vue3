<template>
 <div>
   <h1>ToDoリスト</h1>
   <label><input type="radio" name="task">すべて</label>
   <label><input type="radio" name="task">作業中</label>
   <label><input type="radio" name="task">完了</label>

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
        <tr v-for="(todo,index) in Todos" v-bind:key="index">
            <th>{{ index }}</th>
            <th>{{ todo.task }}</th>
            <th><button>{{ todo.status }}</button></th>
            <th><button>削除</button></th>
        </tr>
      </tbody>
    </table>
   <h2>新規タスクの追加</h2>
   <input type="text" v-model="task"><button @click="log">追加</button>

 </div>
</template>

<script>
export default {
  data() {
    return {
      task: '',
      status: '作業中',
      Todos: []
    }
  },
  methods: {
    log: function() {
      const todoElm = {
        task: this.task,
        status: this.status
      };
      this.Todos.push(todoElm);
    }
  }
};
</script>

<style>

</style>
