<template>
  <div class="app">
    <h1 class="title">Создайте открытку к 8 Марта</h1>
    <CardForm @add-card="addCard" />
    <CardList :cards="cards" />
  </div>
</template>

<script>
import CardForm from './components/CardForm.vue';
import CardList from './components/CardList.vue';

export default {
  components: {
    CardForm,
    CardList,
  },
  data() {
    return {
      cards: [],
    };
  },
  methods: {
    addCard(card) {
      this.cards.push(card);
    },
  },
};
</script>

<style>
body {
  font-family: 'Adigiana 2', cursive;
  background-color: #fff5f5; /* Нежно-розовый фон */
  color: #333;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}


.app {
  display: block;
  margin: auto 0;

  max-width: 800px;
  width: 100%;
  padding: 20px;
  text-align: center;
}

.title {
  color: #ff7eb9; /* Розовый цвет для заголовка */
  font-size: 3rem;
  margin-bottom: 20px;
}
</style>