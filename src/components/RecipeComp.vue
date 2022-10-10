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
  <div class="dd-recipe-done">
      <table>
        <tr v-if="recipes.length > 0">
          <th>Name</th>
          <th>Ingredients</th>
          <th>Steps</th>
        </tr>
        <tr v-for="(r, index) of recipes" :key="r.id">
          <td> <h1>{{ r.name }}</h1> </td>
          <td><div class="content">{{ r.ingredients }}</div></td>
          <td><div class="content">{{ r.steps }}</div></td>
          <td> <button class="dd-delete-btn" type="button" @click="deleteRecipe(index)">Delete</button> </td>
        </tr>
      </table>
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
  margin: 50px;
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

.dd-delete-btn {
  margin: 20px;
}
</style>
