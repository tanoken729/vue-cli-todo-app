<template>
  <div id="app">
    <div class="title">
      <h1>Todoリスト</h1>
    </div>
    <div class="main">
      <div class="switch">
        <label><input type="radio" name="change-displey" onclick="changeDispley()" checked>すべて</label>
        <label><input type="radio" name="change-displey" onclick="changeDispley()" >作業中</label>
        <label><input type="radio" name="change-displey" onclick="changeDispley()" >完了</label>
      </div>
      <div class="task">
        <table>
          <tr>
            <th>ID</th>
            <th>コメント</th>
            <th>状態</th>
          </tr>
          <tr v-for="(list, i) in lists" v-bind:key="i">
            <td>{{ i }}</td>
            <td>{{ list.comment }}</td>
            <td v-if="list.state"><button @click="changeState(i)">作業中</button></td>
            <td v-else><button @click="changeState(i)">完了</button></td>
            <td><button @click="deleteList(i)">削除</button></td>
          </tr>
        </table>
      </div>
    </div>
    <div class="addTask">
      <h1>新規タスクの追加</h1>
        <div class="form">
          <form @submit.prevent>
              <input type="text" v-model="comment">
              <input type="submit" value="送信" @click="addTodo">
          </form>
        </div>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      comment: '',
      lists: [],
    }
  },
  methods: {
    addTodo: function(){
      const todo = {
        comment: this.comment,
        state: true,
      }
      this.lists.push(todo)
    },
    deleteList(i) {
      this.lists.splice(i, 1)
    },
    changeState(i) {
      this.lists[i].state = !this.lists[i].state
    }
  },
};

</script>
