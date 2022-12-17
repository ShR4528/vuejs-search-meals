<template>
  <div class="p-8 pb-0">
    <div class="lex flex-wrap justify-center gap-3 px-8 mb-6">
      <routet-link
        :to="{ name: 'byLetter', params: { letter } }"
        v-for="letter of letters"
        :key="letter"
      >
        {{ letter }}
      </routet-link>
    </div>
  </div>
</template>

<script setup>
import { computed, onMounted } from 'vue';
import store from '../store';
import axiosClient from '../axiosClient.js';

const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split(' ');

onMounted(async () => {
  const response = await axiosClient.get('/list.php?i=list');
});
</script>
