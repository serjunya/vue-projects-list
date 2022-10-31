<template>
  <div class="item">
    <div class="item_head">
        <p class="title">{{ project.title }}</p>
      <div class="delete">
        <button type="button" @click="$emit('delete-project', project)">
          <span class="material-icons">delete</span>
        </button>
      </div>
      <div class="more">
        <button type="button" @click="$emit('show-details', project)">
          <span class="material-icons">more_horiz</span>
        </button>
      </div>
    </div>
    <div class="service">
      <p v-for="microservice in project.microservices">{{ microservice.title }}</p>
    </div>
    <div class="more_details"/>
  </div>
</template>

<script>
export default {
  name: "ProjectInstance",
  props: {
    project: {
      type: Object,
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
  .item_head {
    display: flex;
    flex-direction: row;
  }
  .delete button, .more button {
    border: none;
    background: none;
    margin: 1.5vmin 0 0 3vmin;
  }
  .material-icons {
    font-size: 3vmin;
    color: dimgray;
  }
  .material-icons:hover {
    color: white;
    background-color: dimgray;
    border-radius: 10%;
  }
  .title {
    font-size: 5vmin;
  }
  .service {
    margin-left: 1vmin;
    font-size: 3vmin;
    overflow: hidden;
  }
  .more_details {
    min-height: 10%;
    box-shadow:
    0 -8vmin 11vmin white,
    0 -6.5vmin 8vmin white,
    0 -5vmin 5.5vmin white,
    0 -3.5vmin 3.5vmin white,
    0 -2vmin 2vmin white,
    0 -0.5vmin 1vmin white
  }
  @media screen and (max-width: 480px) {
    .title {
      font-size: 6vmin;
    }
    .material-icons {
      font-size: 4vw;
    }
    .service {
      font-size: 3.5vw;
    }
  }
  @media screen and (max-width: 375px) {
    .title {
      font-size: 12vw;
    }
    .material-icons {
      font-size: 6vw;
    }
    .service {
      font-size: 6vw;
    }
    .item {
      padding: 6vw;
    }
  }
</style>
