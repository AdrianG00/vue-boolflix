<template>
  <div class="col-6 g-0">
    <div class="input-group mb-3">
      <input
        v-model="search"
        @keyup.enter="$emit('performSearch', search)"
        type="text"
        class="form-control"
        placeholder="Cerca per titolo"
        aria-label="Recipient's username"
        aria-describedby="button-addon2"
      />
      <button
        class="btn btn-outline-secondary"
        type="button"
        id="button-addon2"
        @click="cerca"
      >
        <i class="fa-solid fa-magnifying-glass"></i>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  data() {
    return {
      search: "",
    };
  },
  computed: {
    // mysearch(){
    //     return state.search
    // }
  },
  methods: {
    cerca() {
      this.$emit("performSearch", this.search);
      this.search = "";
    },
  },
};
</script>

<style lang="scss">
@import '../styles/general.scss'; 
</style>
