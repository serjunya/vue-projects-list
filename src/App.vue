<template>
  <div class="projects">
    <project-details v-model:show="detailsShown" v-model:project="projectToShow"/>
    <project-list @show-details="showDetails" :projects="projects" @delete-project="deleteProject"/>
    <project-add @create="createProject" :count="count"/>
  </div>
</template>

<script>
import ProjectList from "./components/ProjectList";
import ProjectAdd from "./components/ProjectAdd";
import ProjectDetails from "./components/ProjectDetails";
export default {
  components: {
    'project-list': ProjectList,
    'project-add': ProjectAdd,
    'project-details': ProjectDetails
  },
  name: "App",
  data() {
    return {
      projects: [],
      count: 0,
      detailsShown: false,
      projectToShow: {},
    }
  },
  methods: {
    createProject(newProject) {
      this.projects.push(newProject);
      this.count++;
    },
    deleteProject(project) {
      this.projects = this.projects.filter(p => p.id !== project.id)
    },
    showDetails(project) {
      this.detailsShown = true;
      this.projectToShow = project;
      if (project.id === this.projects[this.projects.length - 1].id) {

      }
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
  @media screen and (max-width: 1080px) {
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
