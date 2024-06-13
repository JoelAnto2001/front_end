<template>
    <div>
      <h1>Math Operations</h1>
      <input v-model.number="num1" placeholder="Number 1" />
      <input v-model.number="num2" placeholder="Number 2" />
      <button @click="performOperation('add')">Add</button>
      <button @click="performOperation('subtract')">Subtract</button>
      <button @click="performOperation('multiply')">Multiply</button>
      <button @click="performOperation('divide')">Divide</button>
      <p>Result: {{ result }}</p>
    </div>
  </template>
  
  <script>
  /* eslint-disable */
  import axios from 'axios';
  
  export default {
    name: 'MathPage',
    props: ['token'],
    data() {
      return {
        num1: 0,
        num2: 0,
        result: null
      };
    },
    methods: {
      async performOperation(operation) {
        try {
          const response = await axios.post(`http://localhost:3000/${operation}`, {
            num1: this.num1,
            num2: this.num2
          }, {
            headers: {
              auth: this.token
            }
          });
          this.result = response.data.result;
        } catch (error) {
          console.error(error);
        }
      }
    }
  };
  </script>
  