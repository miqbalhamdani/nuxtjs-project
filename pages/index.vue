<template>
  <div class="container col-5 d-flex flex-column justify-center mt-5">
    <h1 class="mb-5">
      <a
        href="https://www.iqbalhamdani.id/"
        target="_blank"
        rel="noopener noreferrer"
        :style="linkStyle"
      >
        iqbalhamdani.id
      </a>
    </h1>

    <ul class="list-group">
      <NuxtLink
        v-for="(item, index) in apps"
        :key="index"
        :to="item.slug"
        :style="linkStyle"
      >
        <li class="list-group-item list-group-item-action">
          {{ index+1 }}.
          {{ item.name }}
        </li>
      </NuxtLink>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      apps: [
        { name: 'Todo [Composition API in Nuxt JS]', slug: 'todos' },
      ],
    };
  },

  computed: {
    linkStyle() {
      return {
        'color': '#424242',
        'text-decoration': 'none',
      }
    },
  },
};
</script>
