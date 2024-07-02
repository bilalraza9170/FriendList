<template>
  <li>
    <h2>{{ firstName }}</h2>
    <button @click="toggleFavorite">
      {{ isFavorite ? "Remove from" : "Add to" }} Favorites</button
    ><br /><br />
    <button @click="$emit('delete', id)">Delete</button><br /><br />
    <button @click="toggleDetails">
      {{ detailsAreVisible ? "Hide" : "Show" }} Details
    </button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>Phone:</strong>
        {{ phoneNumber }}
      </li>
      <li>
        <strong>Email:</strong>
        {{ emailAddress }}
      </li>
    </ul>
  </li>
</template>

<script>
export default {
  props: ["id", "firstName", "phoneNumber", "emailAddress", "isFavorite"],
  emits: ["toggle-favorite", "delete"],
  data() {
    return {
      detailsAreVisible: false,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite() {
      this.$emit("toggle-favorite", this.id);
    },
  },
};
</script>
