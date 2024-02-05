<script>
import axios from 'axios';

  export default{
    data() {
      return {
        project: null,
        loading: false,
        baseUrl: "http://127.0.0.1:8000",
      };
    },
    created() {
      console.log(this.$route.params.slug);

      this.loading = true;

      axios
        .get(`${this.baseUrl}/api/projects/${this.$route.params.slug}`)
        .then((resp) => {

          if (resp.data.success) {
            this.project = resp.data.results;
          } else {
            this.$router.push({ name: "not-found" });
          }

        })
        .finally(() => {
          this.loading = false;
        })
    }
  }
</script>

<template>
  <div class="container">
    <h1 class="my-5">{{ project.title }}</h1>

    <h2 v-if="loading">Loading...</h2>
    <div v-else>
      <h3 class="text-warning">Technologies</h3>
      <div v-for="technology in project.technologies" class="d-inline-block">
        <span class="badge text-bg-dark mx-1">{{ technology.name }}</span>
      </div>

      <p class="mt-4"><strong>Description: </strong>{{ project.content }}</p>
    </div>
    
  </div>
  
</template>