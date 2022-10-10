<template>
  <form @submit.prevent="addRecipe">
    <div class="dd-content-recipe">
      <label> Name: </label>
      <input v-model="recipe.name" />
    </div>
    <div class="dd-content-recipe">
      <label> Ingredients: </label>
      <textarea v-model="recipe.ingredients"></textarea>
    </div>
    <div class="dd-content-recipe">
      <label> Steps: </label>
      <textarea v-model="recipe.steps"></textarea>
    </div>
    <button type="submit">Add recipe</button>
  </form>
  <div
      class="dd-recipe-done"
      v-for="(r, index) of recipes" :key="r.id">
        <div>
          <h1>{{ r.name }}</h1>
          <h2>Ingredients: <div class="content">{{ r.ingredients }}</div> </h2>

          <h2>Steps: <div class="content">{{ r.steps }}</div> </h2>

          <button type="button" @click="deleteRecipe(index)">Delete</button>
        </div>
  </div>
</template>

<script>
import { v4 as uuidv4 } from "uuid";
export default {
  name: "App",
  data() {
    return {
      recipe: {
        name: "",
        ingredients: "",
        steps: "",
      },
      recipes: [],
    };
  },
  computed: {
    formValid() {
      const { name, ingredients, steps } = this.recipe;
      return name && ingredients && steps;
    },
  },
  methods: {
    addRecipe() {
      if (!this.formValid) {
        return;
      }
      this.recipes.push({
        id: uuidv4(),
        ...this.recipe,
      });
    },
    deleteRecipe(index) {
      this.recipes.splice(index, 1);
    },
  },
};
</script>

<style>
.content {
  white-space: pre-wrap;
}

.dd-content-recipe {
  display: flex;
  align-items: center;
  justify-content: center;
}

.dd-recipe-done {
  display: flex;
  align-items: center;
  justify-content: center;
}

label {
  margin: 20px;
  width: 100px;
  text-align: start;
}

input {
  margin: 20px;
  width: 200px;
}

textarea {
  margin: 20px;
  width: 200px;
}
</style>
