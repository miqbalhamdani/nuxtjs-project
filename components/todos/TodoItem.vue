<template>
  <div class="card pt-3 pb-2">
    <p>
      <span v-html="isDoneBadge"></span>
      {{ todo.name }}
    </p>
  </div>
</template>

<script>
import { computed } from '@vue/composition-api'

export default {
  name: 'TodoItem',

  props: {
    todo: {
      type: Object,
      required: true,
    },
  },

  setup(props) {
    const isDoneBadge = computed(() => {
      return props.todo.isDone
        ? '<span class="badge rounded-pill bg-success">done</span>'
        : '<span class="badge rounded-pill bg-warning">todo</span>'
    });

    return { isDoneBadge };
  },
};
</script>
