<template>
  <div class="card my-3">
    <div class="p-3">
      <input
        type="text"
        id="input-search"
        class="form-control"
        v-model="keyword"
        placeholder="Enter search"
      >
    </div>
  </div>
</template>

<script>
import { ref, watch } from '@vue/composition-api'

export default {
  name: 'AddTodo',

  setup(props, context) {
    const keyword = ref('');

    watch(keyword, (newValue, oldValue) => {
      setTimeout(() => {
        context.emit('search', newValue)
      }, 500)
    });

    return {
      keyword,
    };
  },
};
</script>
