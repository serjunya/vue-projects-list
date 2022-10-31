<template>
  <button type="button" @click="createProject">
    <span class="material-icons dark">add</span>
  </button>
</template>

<script>
export default {
  name: "ProjectAdd",
  props: {
    count: {
      type: Number,
      required: true
    }
  },
  data() {
    return {
      project: Object
    }
  },
  methods: {
    createProject() {
      this.project = {
        id: Date.now(),
        title: 'Проект ' + (this.count + 1),
        microservices: [
          {title: "Микросервис 1", entities: [
              {title: "Сущность 1"},
              {title: "Сущность 2"},
              {title: "Сущность 3"},
              {title: "Сущность 4"},
            ]},
          {title: "Микросервис 2", entities: [
              {title: "Сущность 1"},
              {title: "Сущность 2"},
              {title: "Сущность 3"},
              {title: "Сущность 4"},
            ]},
          {title: "Микросервис 3", entities: [
              {title: "Сущность 1"},
              {title: "Сущность 2"},
              {title: "Сущность 3"},
              {title: "Сущность 4"},
            ]},
          {title: "Микросервис 4"},
          {title: "Микросервис 5"},
          {title: "Микросервис 6"},
          {title: "Микросервис 7"},
          {title: "Микросервис 8"},
          {title: "Микросервис 9"},
          {title: "Микросервис 10"},
        ]
      }
      this.$emit('create', this.project);
    }
  }
}
</script>

<style scoped>
  button {
    border: none;
    border-radius: 5%;
    background: none;
  }
  button:hover {
    background-color: lightgrey;
  }
  .material-icons {
    font-size: 15vmin;
  }
  @media screen and (max-width: 375px) {
    button svg {
      width: 40vmin;
      height: 40vmin;
    }
  }
</style>
