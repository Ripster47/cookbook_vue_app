<template>
  <div class="recipes-index">
    <h1>All Recipes</h1>
    <div v-for="recipe in recipes">
      <h2>{{ recipe.title }}</h2>
      <router-link v-bind:to="'/recipes/' + recipe.id">
        <img v-bind:src="recipe.image_url" v-bind:alt="recipe.title">
      </router-link>
    </div>
  </div>
</template>

<!-- ========================================= -->

<style>

img{
width: 250px;
}

</style>

<!-- ========================================= -->


<script>
var axios = require('axios');


export default {
  data: function() {
    return {
      recipes: [],
      newRecipeTitle: "",
      newRecipeChef: "",
      newRecipePrepTime: "",
      newRecipeIngredients: "",
      newRecipeDirections: "",
      newRecipeImageUrl: "",
      currentRecipe: {}
    };
  },
  created: function() {
    axios.get("/api/recipes")
      .then(response => {
        this.recipes = response.data;
      });
  },
  methods: {

    }
  };
</script>
