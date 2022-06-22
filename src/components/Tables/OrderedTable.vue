<template>
  <div>
    <ul v-for="post in posts" v-bind:key="post.id">
      <li>{{ post.title }}</li>
      <p>{{ post.description }}</p>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: [],
    };
  },

  methods: {
    async getData() {
      try {
        let response = await fetch("http://localhost:8000/api/allpost");
        this.posts = await response.json();
      } catch (error) {
        console.log(error);
      }
    },
  },

  created() {
    this.getData();
  },
};
</script>
