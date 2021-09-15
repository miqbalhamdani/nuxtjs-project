<template>
  <div class="container mt-5">
    <div class="row d-flex justify-content-center text-center">
      <div class="col-5">
        <AddTodo @add-todo="addTodo"/>

        <FilterTodo @search="setKeyword" />

        <div class="todo-list">
          <TodoItem
            v-for="(todo, index) in todoList"
            :key="index"
            :todo="todo"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import AddTodo from '@/components/todos/AddTodo';
import FilterTodo from '@/components/todos/FilterTodo';
import TodoItem from '@/components/todos/TodoItem';

import { ref, computed } from '@vue/composition-api'

export default ({
  name: 'PageTodos',

  components: {
    AddTodo,
    FilterTodo,
    TodoItem,
  },

  setup() {
    const todos = ref([
      {
        name: 'Lets learn compostion API',
        isDone: true,
      }
    ]);

    function addTodo(payload) {
      todos.value.push(payload);
    };


    const keyword = ref('');

    function setKeyword (payload) {
      keyword.value = payload;
    };


    const todoList = computed(() => {
      const lowerKeyword = keyword.value.toLowerCase();

      return !keyword.value
        ? todos.value
        : todos.value.filter((item) => item.name.toLowerCase().includes(lowerKeyword));
    });

    return {
      todoList,
      addTodo,
      keyword,
      setKeyword,
    };
  },
})
</script>
