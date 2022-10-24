<template>
  <button type="button" @click="createProject">
    <svg width="17vmin" height="17vmin" xmlns="http://www.w3.org/2000/svg">
      <g>
        <rect ry="2%" rx="2%" id="svg_3" height="6%" width="50%" y="42%" x="21%" stroke-linecap="round"
              stroke-linejoin="round" stroke-dasharray="null" stroke-width="0" stroke="#000000" fill="#000000"/>
        <rect id="svg_4" ry="2%" rx="2%" height="50%" width="6%" y="21%" x="42%" stroke-linecap="round"
              stroke-linejoin="round" stroke-dasharray="null" stroke-width="0" stroke="#000000" fill="#000000"/>
      </g>
    </svg>
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
        title: 'Проект ' + (this.count + 1),
        microservices: [
          {title: "Микросервис 1"},
          {title: "Микросервис 2"},
          {title: "Микросервис 3"},
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
    background: none;
  }
  button:hover {
    background-color: lightgrey;
  }
  @media screen and (max-width: 375px) {
    button svg {
      width: 40vmin;
      height: 40vmin;
    }
  }
</style>