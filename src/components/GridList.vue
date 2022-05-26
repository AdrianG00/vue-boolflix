<template>
  <section class="grid-container">
    
      <div
        class="grid-card"
        v-for="(movie, index) in searchAll"
        :key="index"
      >
        <card-component :item="movie" />
      </div>
    
  </section>
</template>

<script>
import { state } from "../store.js";
import CardComponent from "./CardComponent.vue";

export default {
  name: "GridList",
  components: { CardComponent },
  computed: {
    searchAll() {
      return state.searchAll;
    },
  },
};
</script>

<style lang="scss">
@import '../styles/general.scss'; 

.grid-container {
  display: grid;
  grid-template-columns: auto auto auto auto auto;
}
</style>
