<template>
  <h1>Edit Project</h1>
  <form @submit.prevent="updateProject">
    <label>Project Title</label>
    <input type="text" v-model="title" />
    <label>Project Detail</label>
    <textarea v-model="detail"></textarea>
    <button>Update Project</button>
  </form>
</template>

<script>
export default {
  props: ["id"],
  data() {
    return {
      title: "",
      detail: "",
    };
  },
  methods: {
    updateProject() {
      //   console.log("updated project");
      fetch("http://localhost:3000/projects/" + this.id, {
        method: "PATCH",
        headers: {
          Content_type: "application/json",
        },
        body: JSON.stringify({
          title: this.title,
          detail: this.detail,
        }),
      })
        .then(() => {
          this.$router.push("/");
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
  mounted() {
    // console.log()
    fetch("http://localhost:3000/projects/" + this.id)
      .then((res) => {
        // console.log(res);
        return res.json();
      })
      .then((data) => {
        // console.log(data);
        (this.title = data.title), (this.detail = data.detail);
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style></style>
