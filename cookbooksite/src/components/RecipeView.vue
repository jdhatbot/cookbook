<template>
    <div>
      <v-container>
       
      </v-container>  
      
      <h1>{{ recipe.name }}</h1>
      <v-img
        :src="getImage(recipe.image)"
        height="400"
        width="400"
        class="mx-auto"
      ></v-img>
      <h3>{{ recipe.type }}</h3>
      
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
  