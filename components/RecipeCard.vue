<script setup lang="ts">
import { Recipe } from 'types';

defineProps({
    recipe: {
        type: Object as PropType<Recipe>,
        required: true
    }
})
</script>

<template>
<v-card
    class="mx-auto text-capitalize rounded-lg"
    :to="`/dining/recipes/${recipe.id}`"
>
        <v-img
              :src="recipe.img"
              class="align-end"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              height="200px"
              cover
            >
              <v-card-title class="text-white" v-text="recipe.name"></v-card-title>
            </v-img>
    <!-- <template v-slot:title>
        {{ recipe.name }}
        <v-icon color="orange" v-if="recipe.isFavorite">mdi-star</v-icon>
    </template> -->

    <v-card-text>
        <v-list dense>
          
                <!-- Loop through the first three ingredients only -->
                <v-list-item class="text-capitalize" v-for="(ingredient, index) in recipe.ingredients.slice(0, 3)" :key="index">
                    {{ ingredient.name }}
                </v-list-item>
           
            <!-- Display count of remaining ingredients -->
            <v-list-item v-if="recipe.ingredients.length > 3">
              
                    {{ recipe.ingredients.length - 3 }} more...
               
            </v-list-item>
        </v-list>
    </v-card-text>
</v-card>
</template>