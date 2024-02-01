<script>
  export default {
    props: {
      project: Object,
    },
    data() {
      return {}
    },
    computed: {
      truncadetext() {
        if (this.project.content && this.project.content.length > 250) {
          return this.project.content.substring(0, 125) + "...";
        }
      }
      
    }
  }
</script>

<template>
<div class="card h-100">
  <div class="card-body">
    <h5>{{ project.title }}</h5>
  </div>
</div>
</template>

<style lang="scss" scoped></style>