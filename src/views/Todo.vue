<template>
  <div class="todo">
    <h1>Todo List</h1>
    <TodoListInput/>
    <list/>
  </div>
</template>

<script>
import TodoListInput from '@/components/TodoListInput'
export default {
  components: { TodoListInput }
}
</script>

<style scoped>

</style>
