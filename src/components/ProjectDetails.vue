<template>
  <transition name="sidebar-appearance">
    <div class="window" v-if="show" @click="hideDetails">
      <div @click.stop class="sidebar">
        <p class="title">{{ project.title }}</p>
        <div class="contents">
          <div class="microservices" v-for="microservice in project.microservices">
            <div class="m_title">
              <p>{{ microservice.title }}</p>
            </div>
            <div class="entity" v-for="entity in microservice.entities">
              <p>{{ entity.title }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: "ProjectDetails",
  props: {
    show: {
      type: Boolean,
      default: false,
      required: true
    },
    project: {
      type: Object,
      required: true
    }
  },
  methods: {
    hideDetails() {
      this.$emit("update:show", false);
    }
  }
}
</script>

<style scoped>
  .window {
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    position: fixed;
  }
  .sidebar {
    padding: 5vmin;
    width: 40vw;
    height: 100%;
    background: white;
    box-shadow: 0.01vw 0 2vw;
    font-family: Calibri, sans-serif;
  }
  .title {
    font-size: 6vmin;
    margin-bottom: 3vmin;
  }
  .contents {
    border: 1px solid black;
    margin-left: 2%;
    padding: 5%;
    height: 80vh;
    overflow: auto;
  }
  .microservices {
    display: flex;
    flex-direction: column;
    text-align: center;
  }
  .m_title {
    padding: 2%;
    text-align: center;
    line-height: 250%;
    margin-bottom: 2vmin;
    border: 1px solid black;
    height: 10vmin;
    width: 100%;
    font-size: 3vmin;
  }
  .entity {
    border: 1px solid black;
    margin-bottom: 2vmin;
    height: 5vmin;
    align-self: center;
    width: 80%;
    font-size: 2.5vmin;
  }
  .sidebar-appearance-enter-from ,
  .sidebar-appearance-leave-to{
    transform: translate(-40vw);
  }
  .sidebar-appearance-enter-active,
  .sidebar-appearance-leave-active {
    transition: all 0.3s ease;
  }
  @media screen and (max-width: 1080px) {
    .sidebar {
      width: 50vw;
    }
    .sidebar-appearance-enter-from ,
    .sidebar-appearance-leave-to{
      transform: translate(-50vw);
    }
  }
  @media screen and (max-width: 720px) {
    .sidebar {
      width: 100vw;
      height: 60vh;
      box-shadow: 0 -0.01vh 2vh;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      position: absolute;
      bottom: 0;
    }
    .contents {
      height: 90%;
    }
    .sidebar-appearance-enter-from ,
    .sidebar-appearance-leave-to {
      transform: translateY(100vh);
    }
    .sidebar-appearance-enter-active,
    .sidebar-appearance-leave-active {
      transition: all 0.3s ease;
    }
  }
</style>