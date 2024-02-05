<script>
import axios from "axios";
import ProjectCards from "../components/ProjectCards.vue";

export default {
  data() {
    return {
      baseUrl: "http://127.0.0.1:8000",
      projects: [],
    };
  },
  created() {
    axios.get(`${this.baseUrl}/api/projects`).then((resp) => {
      this.projects = resp.data.results;
    });
  },
  components: { ProjectCards },
};
</script>

<template>
  <div class="container">
    <h2 class="text-center py-5 text-uppercase">Project List</h2>

    <div class="row row-cols-1 row-cols-md-2 row-cols-lg-4 g-3">
      <div class="col" v-for="project in projects" :key="project.id">
        <ProjectCards :project="project" />
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped></style>
