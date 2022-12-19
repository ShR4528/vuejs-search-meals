<template>
  <!-- <div class="p-8">
    <h1 class="text-4xl font-bold mb-4">Ingredients</h1>
    <router-link
      :to="{
        name: 'byIngredient',
        params: { ingredient: ingredient.idIngredient },
      }"
      v-for="ingredient of ingredients"
      :key="ingredient.idIngredient"
      class="block bg-white rounded p-3 mb-3 shadow"
    >
      <h3 class="text-2-xl font-bold mb-2">{{ ingredient.strIngredient }}</h3>
      <p>{{ ingredient.strDescription }}</p>
    </router-link>
  </div> -->
  <Meals :meals="meals" />
</template>

<script setup>
import { computed } from '@vue/reactivity'
import { onMounted, ref } from 'vue'
import { useRoute } from 'vue-router'
import store from '../store'
import Meals from '../components/Meals.vue'

const route = useRoute()
const ingredient = computed(() => store.state.ingredient)

const meals = computed(() => store.state.mealsByIngredient)
onMounted(() => {
  store.dispatch('searchMealsByIngredient', route.params.ingredient)
})
</script>
