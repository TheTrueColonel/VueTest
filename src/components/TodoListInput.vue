<template>
  <div class="todolist">
    <input type="text" v-model="msg">
    <button @click="Create">Create</button>
    <TodoList :TodoLists="TodoLists" :Delete="Delete"/>
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import { ref } from '@vue/runtime-core'

export default {
  components: { TodoList },
  setup () {
    let data = []
    if (JSON.parse(localStorage.getItem('todoItems')) == null) {
      data = [
        { id: 1, name: 'Learn Vue' },
        { id: 2, name: 'Google Errors' },
        { id: 3, name: 'Repeat' }
      ]
      localStorage.setItem('idRef', '4')
      localStorage.setItem('todoItems', JSON.stringify(data))
    } else {
      data = JSON.parse(localStorage.getItem('todoItems'))
    }
    return {
      TodoLists: ref(data)
    }
  },
  methods: {
    Create () {
      let id = parseInt(localStorage.getItem('idRef'))
      localStorage.setItem('idRef', (id += 1).toString())
      const next = { id, name: this.msg }
      this.TodoLists.push(next)
      localStorage.setItem('todoItems', JSON.stringify(this.TodoLists))
    },
    Delete (idx) {
      this.TodoLists = this.TodoLists.filter((r) => r.id !== idx)
      localStorage.setItem('todoItems', JSON.stringify(this.TodoLists))
    }
  }
}
</script>

<style lang="css" scoped>
.todolist{
  width: 17%;
  margin-left: auto;
  margin-right: auto;
}
.container {
  font-size: 20px;
  display: block;
}
input {
  font-size: 20px;
  border-radius: 5px;
  margin-right: 5%;
}
button {
  border-radius: 5px;
  font-size: 20px;
  cursor: pointer;
}
</style>
