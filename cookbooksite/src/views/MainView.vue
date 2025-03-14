<script setup>
import { ref } from 'vue'
import { VTextField, VList, VCard, VCardText, VImg } from 'vuetify/components'

const items = ref([
  { id: 1, title: 'Card 1', description: 'Description for card 1.' },
  { id: 2, title: 'Card 2', description: 'Description for card 2.' },
  { id: 3, title: 'Card 3', description: 'Description for card 3.' },
])
</script>

<template>
  <div class="main-view">
    <h1>Family Cookbook</h1>
    <v-text-field
      append-inner-icon="mdi-magnify"
      label="Search Recipes"
      variant="solo"
      hide-details
      single-line
    ></v-text-field>

    <v-card class="mx-auto my-8" elevation="16" max-width="344">
      <v-img
        color="surface-variant"
        height="200"
        src="https://cdn.vuetifyjs.com/docs/images/cards/purple-flowers.jpg"
        cover
      ></v-img>
      <v-card-text>Recipe 1</v-card-text>
    </v-card>
  </div>
</template>

<style scoped>
.main-view {
  text-align: center;
  margin-top: 50px;
}

h1 {
  font-size: 2.5em;
  color: #333;
}

p {
  font-size: 1.2em;
  color: #666;
}
</style>
