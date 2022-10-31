<template>
  <project-instance
      v-for="project in projects"
      :project="project"
      :key="project.id"
      @delete-project="$emit('delete-project', project)"
      @show-details="$emit('show-details', project)"
  />
</template>

<script>
import ProjectInstance from "./ProjectInstance";
export default {
  name: "ProjectList",
  components: {
    'project-instance': ProjectInstance
  },
  props: {
    projects: {
      type: Array,
      required: true
    }
  }
}
</script>
