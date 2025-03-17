<script setup>
import { ref, watch } from "vue";
import srcquiz from "./data/quizes.json";
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
    <div v-for="quiz in quizes" :key="quiz.id"  class="card">
      <img :src="quiz.img" 
      :alt="quiz.title">
      <div class="card-body">
        <h2>{{quiz.title}}</h2>
        <p>{{ quiz.questions.length }} Question</p>
      </div>
    </div>
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

.card {
  width: 270px;
  margin-right: 30px;
  margin-bottom: 30px;
  border-radius: 5px;
  overflow: hidden;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.1) ;
}

.card img {
  width: 100%;
  height: 200px;
  object-fit: cover;
  margin:0;
}

.card-body {
  padding: 0 15px;
}

.card-body h2 {
  font-weight: bold;
}
</style>