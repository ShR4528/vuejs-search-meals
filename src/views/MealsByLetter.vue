<template>
  <div class="flex justify-center gap-2 mt-2">
    <routet-link
      :to="{ name: 'byLetter', params: { letter } }"
      v-for="letter of letters"
      :key="letter"
      class="w-2 h-2 flex items-center justify-center hover:text-orange-500 hover:scale-150 transition-all"
    >
      {{ letter }}
    </routet-link>
  </div>
  <Meals :meals="meals" />
</template>

<script setup>
import store from '../store'
import Meals from '../components/Meals.vue'
import { onMounted, watch } from 'vue'
import { computed } from '@vue/reactivity'
import { useRoute } from 'vue-router'

const route = useRoute()
const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('')
const meals = computed(() => store.state.mealsByLetter)

watch(route, () => {
  store.dispatch('searchMealsByLetter', route.params.letter)
})

onMounted(() => {
  store.dispatch('searchMealsByLetter', route.params.letter)
})
</script>
