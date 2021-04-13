<template>
  <div class="container">
    <h1>Threads</h1>

    <hr />
    <FormTodo v-on:add-todo="addComment"></FormTodo>
    <h1>Replies:</h1>
    <div class="list-group">
      <div
        class="list-group-item"
        v-for="(Comments, index) in comments"
        v-bind:key="index"
      >
        <span class="comments_author">
          <strong>{{ Comments.name }}</strong
          >:</span
        >
        <p class="ml-5 ml-lg-0"></p>
        <p>{{ Comments.message }}</p>
        <div>
          <a href="#" title="Excluir" v-on:click="removeComment(index)"
            >Excluir</a
          >
        </div>
      </div>

      <div class="row mx-md-n5">
        <div class="col py-3 px-md-5 bordered col-example"></div>
        <div class="col py-3 px-md-5 bordered col-example"></div>
      </div>
    </div>
  </div>
</template>
<script>
import FormTodo from "./FormTodo";
export default {
  components: {
    FormTodo,
  },
  data() {
    return {
      comments: [],
    };
  },
  methods: {
    addComment(comment) {
      this.comments.push(comment);
    },
    removeComment(index) {
      this.comments.splice(index, 1);
    },
  },
};
</script>
