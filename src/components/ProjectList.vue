<template>
  <div class="item" v-for="project in projects">
    <div class="p_title">
      <p>{{ project.title }}</p>
    </div>
    <div class="p_service">
      <p v-for="microservice in project.microservices">{{ microservice.title }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProjectList",
  props: {
    projects: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>
  .item {
    display: flex;
    flex-direction: column;
    padding: 3vmin;
    border: 2px solid black;
    font-family: Calibri, sans-serif;
  }
  .p_title {
    font-size: 5vmin;
  }
  .p_service {
    margin-left: 1vmin;
    font-size: 3vmin;
    overflow: auto;
  }
  @media screen and (max-width: 480px) {
    .p_title {
      font-size: 8vw;
    }
    .p_service {
      font-size: 3.5vw;
    }
  }
  @media screen and (max-width: 375px) {
    .p_title {
      font-size: 12vw;
    }
    .p_service {
      font-size: 6vw;
    }
    .item {
      padding: 6vw;
    }
  }
</style>