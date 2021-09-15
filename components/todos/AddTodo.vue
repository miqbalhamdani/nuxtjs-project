<template>
  <div class="card">
    <div class="p-3">
      <label
        for="input-todo"
        class="form-label"
      >Todo Name</label>

      <input
        type="text"
        id="input-todo"
        class="form-control"
        v-model="name"
        placeholder="Enter todo"
      >

      <button
        type="button"
        class="btn btn-primary float-end mt-3"
        @click="addTodo"
      >Add</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AddTodo',

  data() {
    return {
      name: '',
    };
  },

  methods: {
    addTodo() {
      this.$emit('add-todo', {
        name: this.name,
        isDone: false,
      });
    },
  },
};
</script>


