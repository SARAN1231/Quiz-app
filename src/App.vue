<script setup>
import q from "./data/quizes.json"
import { ref,watch} from "vue";
import Card from "./components/Card.vue";
const quizes = ref(q);
const search = ref("");

watch(search,() => {
  quizes.value = q.filter(quiz => quiz.name.toLowerCase().includes(search.value.toLowerCase()))
})

</script>

<template>
  <main>
  <div class="container">
    <header>
      <h1>Quizes</h1>
      <input v-model.trim="search" type="text" placeholder="search">
    </header>
    <div class="options-container">
      <Card  v-for="quiz in quizes" :key="quiz.id" :quiz="quiz"/>
    </div>
  </div>
</main>
</template>

<style scoped>
  main {
    height: 100vh;
     background: url("https://t4.ftcdn.net/jpg/04/39/13/37/360_F_439133763_FrLdhZsd5aGC23r9ATARuKJBr8ifZjIe.jpg");
     background-repeat: no-repeat;
  background-size: cover;
   background-position: center;
   overflow: hidden;
   overflow-y: scroll;
  }
  .container {
    max-width: 1000px;
    margin: 0 auto;
    }
  header {
    margin-bottom: 10px;
    margin-top: 30px;
    display: flex;
    align-items: center;
  }
  header h1 {
    font-weight: bold;
    margin-right: 30px;
    font-size: 50px;
  }
  header input {
    border: none;
    background-color: rgba(128,128,128,0.2);
    padding: 10px;
    border-radius: 5px;
  }
  .options-container{
    display: flex;
    flex-wrap: wrap;
    margin-top: 40px;
  }

</style>