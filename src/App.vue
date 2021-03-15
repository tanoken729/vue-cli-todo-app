<template>
  <div id="app">
    <h1>Todoリスト</h1>
    <div>
      <label><input type="radio" name="change-displey" onclick="changeDispley();" checked>すべて</label>
      <label><input type="radio" name="change-displey" onclick="changeDispley();" >作業中</label>
      <label><input type="radio" name="change-displey" onclick="changeDispley();" >完了</label>
      <table>
        <tr>
          <th>ID</th>
          <th>コメント</th>
          <th>状態</th>
        </tr>
        <tr v-for="(list, i) in lists" v-bind:key="i">
          <td>{{ i }}</td>
          <td>{{ list }}</td>
          <td><button>作業中</button></td>
          <td><button>削除</button></td>
        </tr>
      </table>
    </div>
    <h1>新規タスクの追加</h1>
    <div>
      <form @submit.prevent>
          <input type="text" v-model="comment">
          <input type="submit" value="送信" @click="addTodo">
      </form>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      comment: '',
      lists: []
    }
  },
  methods: {
    addTodo: function(){
      this.lists.push(this.comment)
    },
  },
};

</script>