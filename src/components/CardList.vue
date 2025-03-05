<template>
    <div class="card-list">
      <div v-for="(card, index) in cards" :key="index" class="card">
        <p class="card-from">От: {{ card.from }}</p>
        <p class="card-message">{{ card.message }}</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      cards: {
        type: Array,
        required: true,
      },
    },
  };
  </script>
  
  <style>
  .card-list {
    margin-top: 30px;
    display: flex;
    flex-direction: column;
    gap: 20px;
    align-items: center;
    width: 100%;
  }
  
  .card {
    background-color: white;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    animation: fadeIn 0.5s ease;
    width: 100%;
    max-width: 400px;
  }
  
  .card-from {
    font-weight: bold;
    color: #ff7eb9;
    margin-bottom: 10px;
  }
  
  .card-message {
    color: #333;
    line-height: 1.5;
  }
  
  @keyframes fadeIn {
    from {
      opacity: 0;
      transform: translateY(20px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }
  </style>