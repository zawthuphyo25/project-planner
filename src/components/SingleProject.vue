<template>
  <div class="project" :class="{ complete: project.complete }">
    <div class="flexing">
      <h3 @click="showDetail = !showDetail">{{ project.title }}</h3>
      <div>
        <!-- Delete Project -->
        <i class="ri-delete-bin-2-fill icon" @click="deleteProject"></i>
        <!-- Edit Project -->
        <router-link :to="{ name: 'editProject', params: { id: project.id } }">
          <i class="ri-pencil-fill icon"></i>
        </router-link>
        <!-- Complete Project -->
        <i class="ri-check-fill icon" @click="completeProject"></i>
      </div>
    </div>

    <p v-if="showDetail">{{ project.detail }}</p>
  </div>
</template>

<script>
export default {
  props: ["project"],
  data() {
    return {
      showDetail: false,
      api: "http://localhost:3000/projects/",
    };
  },
  methods: {
    deleteProject() {
      // console.log("deleted");
      let deleteRoute = this.api + this.project.id;
      // console.log(this.api + this.project.id);
      fetch(deleteRoute, { method: "DELETE" })
        .then(() => {
          this.$emit("delete", this.project.id);
        })
        .catch((err) => {
          console.log(err);
        });
    },
    completeProject() {
      let updateCompleteRoute = this.api + this.project.id;
      // console.log(updateCompleteRoute);
      fetch(updateCompleteRoute, {
        method: "PATCH",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          complete: !this.project.complete,
        }),
      })
        .then(() => {
          this.$emit("complete", this.project.id);
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>

<style>
.project {
  padding: 20px;
  background-color: #f2f2f2;
  margin: 10px;
  border-left: 8px solid crimson;
  border-radius: 8px;
}
h3 {
  color: indigo;
  cursor: pointer;
}
.flexing {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.icon {
  margin-left: 10px;
  cursor: pointer;
  transition: 0.3s ease-in-out;
}
.icon:hover {
  color: #777;
}
.complete {
  border-left-color: green;
}
a {
  text-decoration: none;
  color: #2c3e50;
}
</style>
