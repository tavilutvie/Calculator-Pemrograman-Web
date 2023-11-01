<template>
  <div class="calculator">
    <input v-model="operand1" type="text" placeholder="Operand 1" />
    <input v-model="operand2" type="text" placeholder="Operand 2" />
    <div class="operation-buttons">
      <button @click="performOperation('+')">+</button>
      <button @click="performOperation('-')">-</button>
      <button @click="performOperation('*')">*</button>
      <button @click="performOperation('/')">/</button>
    </div>
    <div class="result">
      Result: {{ result }}
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      operand1: '',
      operand2: '',
      result: '',
    };
  },
  methods: {
    performOperation(operator) {
      const num1 = parseFloat(this.operand1);
      const num2 = parseFloat(this.operand2);

      if (isNaN(num1) || isNaN(num2)) {
        this.result = 'Invalid input';
      } else {
        switch (operator) {
          case '+':
            this.result = num1 + num2;
            break;
          case '-':
            this.result = num1 - num2;
            break;
          case '*':
            this.result = num1 * num2;
            break;
          case '/':
            if (num2 !== 0) {
              this.result = num1 / num2;
            } else {
              this.result = 'Division by zero';
            }
            break;
          default:
            this.result = 'Invalid operator';
        }
      }
    },
  },
};
</script>
