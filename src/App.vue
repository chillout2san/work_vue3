<template>
 <div>
   <h1>ToDoリスト</h1>
   <label><input type="radio" name="task" @click="display = 'すべて'" checked>すべて</label>
   <label><input type="radio" name="task" @click="display = '作業中'">作業中</label>
   <label><input type="radio" name="task" @click="display = '完了'">完了</label>

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
        <tr v-for="(todo,index) in Todos" v-bind:key="index" v-show="display===todo.status || display==='すべて'">
            <th>{{ index }}</th>
            <th>{{ todo.task }}</th>
            <th><button @click="changeStatus(index)">{{ todo.status }}</button></th>
            <th><button @click="deleteTask(index)">削除</button></th>
        </tr>
      </tbody>
    </table>
   <h2>新規タスクの追加</h2>
   <input type="text" v-model="task"><button @click="pushTask">追加</button>

 </div>
</template>

<script>
export default {
  data() {
    return {
      task: '',
      status: '作業中',
      display: 'すべて',
      Todos: []
    }
  },
  methods: {
    pushTask: function() {
      const todoElm = {
        task: this.task,
        status: this.status
      };
      this.Todos.push(todoElm);
      this.task = '';
    },
    deleteTask: function(index) {
      this.Todos.splice(index, 1);
    },
    changeStatus: function(index) {
      if(this.Todos[index].status === '作業中'){
        this.Todos[index].status = '完了';
      }else{
        this.Todos[index].status = '作業中';
      }
    }
  }
};
</script>

<style>

</style>
