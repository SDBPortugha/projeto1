<template>
  <div class="form-todo form-gourp">
    <form @submit.prevent="addComment">
      <p>
        <input
          placeholder="Name:"
          type="text"
          name="author"
          class="form-control"
          v-model="name"
          required
        />
      </p>
      <p>
        <textarea
          placeholder="Here is your answer:"
          name="message"
          class="form-control"
          v-model="message"
          required
        ></textarea>
      </p>

      <button type="submit" class="btn btn-primary">Send</button>
      <div class="row mx-md-n5">
        <div class="col py-3 px-md-5 bordered col-example"></div>
        <div class="col py-3 px-md-5 bordered col-example"></div>
      </div>
    </form>
  </div>
</template>
<script>
export default {
  data() {
    return {
      name: "",
      message: "",
    };
  },
  methods: {
    addComment() {
      this.$emit("add-todo", {
        name: this.name,
        message: this.message,
      });
      this.name = "";
      this.message = "";
    },
  },
};
</script>
