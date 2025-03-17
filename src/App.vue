<script setup>
import { ref } from "vue";
import srcquiz from "./data/quizes.json";
const quizes = ref(srcquiz);
console.log(quizes)
</script>

<template>
  <main>
   <header>
    <h1 id="title">QuizVue</h1>
    <input id="search-input" type="text">
   </header> 
   <section id="quiz-container">
    <div v-for="quiz in quizes" :key="quiz.id"  class="card">
      <img src="/public/img-programming.jpg" alt="Programming">
      <div class="card-body">
        <h2>Programming</h2>
        <p>2 Qestion</p>
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