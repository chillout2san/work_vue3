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
        <tr>
          <th></th>
          <th></th>
          <th></th>
          <th></th>
        </tr>
      </tbody>
    </table>
   <h2>新規タスクの追加</h2>
   <input type="text"><button @click="log">追加</button>

 </div>
</template>

<script>
export default {
  data() {
    return {
      Todos: ['テスト']
    }
  },
  methods: {
    log: function() {
      console.log(this.Todos);
    }
  }
};
</script>

<style>

</style>
