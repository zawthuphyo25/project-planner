<template>
  <div class="project">
    <div class="flexing">
      <h3 @click="showDetail = !showDetail">{{ project.title }}</h3>
      <div>
        <i class="ri-delete-bin-2-fill icon"></i>
        <i class="ri-pencil-fill icon"></i>
        <i class="ri-check-fill icon"></i>
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
    };
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
</style>
