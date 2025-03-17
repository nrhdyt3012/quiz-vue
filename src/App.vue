<script setup>
import { ref, watch } from "vue";
import srcquiz from "./data/quizes.json";

import QuizCard from "./components/QuizCard.vue";
const quizes = ref(srcquiz);
const search = ref("")

watch(search, () => {
  quizes.value = srcquiz.filter((quiz) => {
    return quiz.title.toLowerCase().includes(search.value.toLowerCase());
  });
});
</script>

<template>
  <main>
   <header>
    <h1 id="title">QuizVue</h1>
    <input v-model="search" id="search-input" type="text">
   </header> 
   <section id="quiz-container">
    <!-- <div >
      <img :src="quiz.img" 
      :alt="quiz.title">
      <div class="card-body">
        <h2>{{quiz.title}}</h2>
        <p>{{ quiz.questions.length }} Question</p>
      </div>
    </div> -->
    <QuizCard v-for="quiz in quizes" :key="quiz.id"  class="card"/>
   </section>
  </main>
</template>

<style scoped>
main {
  max-width: 900px;
  margin: 0 auto;
}

header {
  margin-top: 30px;
  margin-bottom:10px;
  display: flex;
  align-items: center;
}

#title {
  font-weight: bold;
  margin-right: 30px;

}

#search-input {
  border: none;
  background-color: #c9c9c9a9;
  padding: 10px;
  border-radius: 5%;
}

#quiz-container {
  display: flex;
  flex-wrap: wrap;
  margin-top: 20px;
}

</style>