<template>
    <div class="card-form">
      <input
        v-model="from"
        type="text"
        placeholder="От кого"
        class="input"
      />
      <textarea
        v-model="message"
        placeholder="Ваше поздравление"
        class="textarea"
      ></textarea>
      <select v-model="selectedTemplate" class="select">
        <option value="">Выберите шаблон (необязательно)</option>
        <option v-for="(template, index) in templates" :key="index" :value="template">
          {{ template }}
        </option>
      </select>
      <button @click="submitCard" :disabled="isButtonDisabled" class="button">
        Отправить
      </button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        from: '',
        message: '',
        selectedTemplate: '',
        templates: [
          'Самой доброй жене',
          'Наикрасивейшей маме',
          'Лучшей подруге',
          'Самой милой бабушке',
        ],
      };
    },
    computed: {
      isButtonDisabled() {
        return !this.from || !this.message;
      },
    },
    methods: {
      submitCard() {
        if (this.selectedTemplate) {
          this.message += ` ${this.selectedTemplate}`;
        }
        this.$emit('add-card', {
          from: this.from,
          message: this.message,
        });
        this.from = '';
        this.message = '';
        this.selectedTemplate = '';
      },
    },
  };
  </script>
  
  <style>
  .card-form {
    display: flex;
    flex-direction: column;
    gap: 15px;
    align-items: center;
  }
  
  .input,
  .textarea,
  .select {
    padding: 10px;
    border: 1px solid #ff7eb9;
    border-radius: 5px;
    font-size: 1rem;
    background-color: white;
    color: #333;
    width: 100%;
    max-width: 400px;
    font-family: 'Adigiana 2', cursive;
  }
  
  .textarea {
    resize: vertical;
    min-height: 100px;
  }
  
  .button {
    padding: 10px 20px;
    background-color: #ff7eb9;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 1rem;
    transition: background-color 0.3s ease;
    font-family: 'Adigiana 2', cursive;
  }
  
  .button:disabled {
    background-color: #ccc;
    cursor: not-allowed;
  }
  
  .button:hover:not(:disabled) {
    background-color: #ff5c8d;
  }
  </style>