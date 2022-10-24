<template>
  <div class="app">
    <div class="projects">
      <project-list :projects="projects"/>
      <project_add @create="createProject" :count="projects.length"/>
    </div>
  </div>
</template>

<script>
import ProjectList from "./components/ProjectList";
import ProjectAdd from "./components/ProjectAdd";
export default {
  components: {
    'project-list': ProjectList,
    'project_add': ProjectAdd
  },
  name: "App",
  data() {
    return {
      projects: [],
    }
  },
  methods: {
    createProject(newProject) {
      this.projects.push(newProject);
    }
  }
}
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  .projects {
    margin: 2vw;
    display: grid;
    grid-auto-rows: 40vh;
    grid-template-columns: repeat(4, 1fr);
    grid-gap: 2vw;
  }
  @media screen and (max-width: 960px) {
    .projects {
      grid-template-columns: repeat(2, 1fr);
    }
  }
  @media screen and (max-width: 375px) {
    .projects {
      grid-template-columns: 100%;
    }
  }
</style>