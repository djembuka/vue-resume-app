<template>
  <div class="loader" v-if="loader"></div>
  <div v-else>
    <div class="card" v-if="comments.length">
      <h2>Комментарии</h2>
      <ul class="list">
        <li class="list-item" v-for="comment in comments" :key="comment.id">
          <div>
            <p>
              <strong>{{ comment.email }}</strong>
            </p>
            <small>{{ comment.body }}</small>
          </div>
        </li>
      </ul>
    </div>
    <p v-else>
      <button class="btn primary" @click="loadComments">
        Загрузить комментарии
      </button>
    </p>
  </div>
</template>

<script>
export default {
  name: 'AppComments',
  data() {
    return {
      comments: [],
      loader: false,
    };
  },
  methods: {
    async loadComments() {
      this.loader = true;
      const response = await fetch(
        'https://jsonplaceholder.typicode.com/comments?_limit=42'
      );
      const result = await response.json();

      this.loader = false;
      this.comments = result;
    },
  },
};
</script>
