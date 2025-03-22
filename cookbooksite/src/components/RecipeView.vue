<template>
    <div>
      <v-container>
        <v-row>
          <v-col cols="12" align="center">
            <h1>{{ recipe.name }}</h1>
          </v-col>
        </v-row>
        <!-- <v-row>
          <v-col cols="12" align="center">
            <v-img
              :src="getImage(recipe.image)"
              height="400"
              width="400"
              class="mx-auto"
            ></v-img>
          </v-col>
        </v-row> -->
        <v-row>
          <v-col cols="12" align="center">
            <h3>{{ recipe.type }}</h3>
          </v-col>
        </v-row>
       <v-row>
        <v-col>
          <v-card>
            <v-card-title>Ingredients</v-card-title>
            <v-card-text>
              <v-list>
                <v-list-item v-for="ingredient in recipe.ingredients" :key="ingredient.index">
                  
                    <v-list-item-title class="text-wrap">{{ ingredient.ingredientText }}</v-list-item-title>
                  
                </v-list-item>
              </v-list>
            </v-card-text>
          </v-card>
        </v-col>
        <v-col>
          <v-card>
            <v-card-title>Instructions</v-card-title>
            <v-card-text>
              <v-list>
                <v-list-item v-for="(instruction, index) in recipe.directions" :key="index">
                  
                    <v-list-item-title class="text-wrap">{{ instruction }}</v-list-item-title>
                  
                </v-list-item>
              </v-list>
            </v-card-text>
          </v-card>
        </v-col>
       </v-row>
       <v-row>
        <p>Credit To: {{ recipe.creditTo }}</p>
       </v-row>
      </v-container>  
      

  </div>
  </template>
  
<script setup>
  import { computed, ref } from 'vue'
import { VTextField, VList, VCard, VCardText, VImg } from 'vuetify/components'
import {recipesData} from '../data/recipes'

const props = defineProps({id: String});

    const recipes = ref(recipesData);
    
  const recipe = ref(computed(() => {
    return recipes.value.find((recipe) => recipe.id === props.id);
  }).value);

const getImage = (image) => {
  return new URL(`../recipeImages/${image}`, import.meta.url).href;
}

</script>
  