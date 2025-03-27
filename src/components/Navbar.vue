<template>
  <nav class="main-nav">
    <router-link to="/">Projects</router-link>
    <div class="line">|</div>
    <router-link :to="{ name: 'addProject' }">Add Project</router-link>
  </nav>
</template>

<script>
export default {};
</script>

<style>
.main-nav {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 40px auto;
}
.main-nav a {
  display: inline-block;
  text-decoration: none;
  margin: 0 10px;
  color: #999;
  font-size: 18px;
}
a.router-link-active {
  border-bottom: 2px solid#00ce89;
  padding-bottom: 4px;
}
.line {
  color: #999;
}
</style>
