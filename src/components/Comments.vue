<template>
  <div class="container">
    <h1>Comentários</h1>
    <hr />
    <div class="form-todo form-gourp">
      <form @submit.prevent="addComment">
        <p>
          <input
            placeholder="Nome"
            type="text"
            name="author"
            class="form-control"
            v-model="name"
            required
          />
        </p>
        <p>
          <textarea
            placeholder="Comentário"
            name="message"
            class="form-control"
            v-model="message"
            required
          ></textarea>
        </p>
        <button type="submit" class="btn btn-primary">Comentar</button>
      </form>
    </div>
    <div class="list-group">
      <div
        class="list-group-item"
        v-for="(Comments, index) in comments"
        v-bind:key="index"
      >
        <span class="comments_author"
          >Autor: <strong>{{ Comments.name }}</strong></span
        >
        <p>{{ Comments.message }}</p>
        <div>
          <a href="#" title="Excluir" v-on:click="removeComment(index)"
            >Excluir</a
          >
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      comments: [],
      name: "",
      message: "",
    };
  },
  methods: {
    addComment() {
      this.comments.push({
        name: this.name,
        message: this.message,
      });
      this.name = "";
      this.message = "";
    },
    removeComment(index) {
      this.comments.splice(index, 1);
    },
  },
};
</script>
