<template>
    <div class="main-view">
      <v-container>
        <v-row>
          <v-col cols="12" align="center">
            <h1>Family Cookbook</h1>
          </v-col>
        </v-row>
        <v-row>
          <v-spacer></v-spacer>
          <v-col cols="3" align="center">
            <v-text-field
              append-inner-icon="mdi-magnify"
              label="Search Recipes"
              variant="solo"
              hide-details
              single-line
            ></v-text-field>
          </v-col>
          <v-spacer></v-spacer>
        </v-row>
      </v-container>
      <v-container>
        <v-row>
        <v-col
          v-for="recipe in recipes"
          :key="recipe.id"
          cols="12"
          md="4"
        >
          <v-card class="mx-auto my-8" elevation="16" max-width="344" @click="goToRecipe(recipe)">
            <v-img
              color="surface-variant"
              height="200"
              :src="getImage(recipe.image)"
              cover
            ></v-img>
            <v-card-text>{{ recipe.name }}</v-card-text>
          </v-card>
        </v-col>
      </v-row>
      </v-container>
   
  </div>
  </template>
  
<script setup>
  import { computed, ref } from 'vue'
import { VTextField, VList, VCard, VCardText, VImg } from 'vuetify/components'
import router from "@/router";

import {recipesData} from '../data/recipes'

const recipes = ref(recipesData);

const getImage = (image) => {
  return new URL(`../recipeImages/${image}`, import.meta.url).href
}
const goToRecipe = (recipe) => {
  router.push({ name: 'recipe', params: { id: recipe.id} });
}
</script>
  