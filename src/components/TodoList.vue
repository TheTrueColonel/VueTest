<template>
  <ul>
    <li v-for="(todolist, index) in TodoLists" :key="index">
      <span class="name">{{todolist.name}}</span>
      <span class="delete" @click="Delete(todolist.id)">x</span>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    TodoLists: Array,
    Delete: Function
  }
}
</script>

<style scoped>
  ul {
    list-style: none;
    flex-direction: column;
    width: 100%;
    margin: auto;
    padding: 0;
  }
  li {
    display: flex;
    margin: 5px 0;
    justify-content: space-between;
    align-content: center;
  }
  .name {
    font-weight: bold;
  }
  .delete {
    background-color: #ff4d4d;
    color: white;
    padding: 4px 8px;
    line-height: 1;
    border-radius: 3px;
    cursor: pointer;
  }
  .delete:hover {
    background-color: #ff1a1a;
  }
</style>
