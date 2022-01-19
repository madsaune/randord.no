<template>
  <div class="generator">
    <form @submit.prevent="generate()">
      <div class="grid">
        <input type="number" max="1000" v-model="numWords" />
        <button>Generer</button>
      </div>
    </form>

    <div class="wordlist">
      <span v-for="word in listOfWords" :key="word">{{ word }}, </span>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
import { wordlist } from "@/data/wordlist.js";

export default {
  setup() {
    let numWords = ref(1);
    let listOfWords = ref([]);

    function generate() {
      listOfWords.value = [];
      for (let i = 0; i < numWords.value; i += 1) {
        listOfWords.value.push(wordlist[randomIntMinMax(0, wordlist.length)]);
      }
    }

    function randomIntMinMax(min, max) {
      min = Math.ceil(min);
      max = Math.floor(max);
      return Math.floor(Math.random() * (max - min) + min);
    }

    return {
      numWords,
      listOfWords,
      generate,
    };
  },
};
</script>

<style scoped>
.wordlist {
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: center;
}
span {
  display: block;
  text-align: center;
}
</style>
