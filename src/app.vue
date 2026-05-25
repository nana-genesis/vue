<template>
  <div class="container">
    <h1>Calculadora Aritmética</h1>
    <div class="calculadora">
      <div class="input-group">
        <label>Número 1:</label>
        <input
          type="number"
          v-model.number="numero1"
          placeholder="Digite o primeiro número"
        />
      </div>

      <div class="input-group">
        <label>Operação:</label>
        <select v-model="operacao">
          <option value="soma">➕ Soma (+)</option>
          <option value="subtracao">➖ Subtração (-)</option>
          <option value="multiplicacao">✖️ Multiplicação (×)</option>
          <option value="divisao">➗ Divisão (÷)</option>
        </select>
      </div>

      <div class="input-group">
        <label>Número 2:</label>
        <input
          type="number"
          v-model.number="numero2"
          placeholder="Digite o segundo número"
        />
      </div>

      <div class="resultado">
        <h2>Resultado:</h2>
        <div class="valor-resultado">{{ resultado }}</div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'App',
  data() {
    return {
      numero1: 0,
      numero2: 0,
      operacao: 'soma' as string,
    }
  },
  computed: {
    resultado(): number | string {
      const n1 = this.numero1
      const n2 = this.numero2
      switch (this.operacao) {
        case 'soma':
          return n1 + n2
        case 'subtracao':
          return n1 - n2
        case 'multiplicacao':
          return n1 * n2
        case 'divisao':
          return n2 === 0 ? 'Erro: Divisão por zero!' : n1 / n2
        default:
          return 0
      }
    },
  },
})
</script>

<style scoped>
.container {
  max-width: 500px;
  margin: 50px auto;
  padding: 20px;
  font-family: Arial, sans-serif;
}

h1 {
  text-align: center;
  color: #42b983;
}

.calculadora {
  background: #f5f5f5;
  padding: 30px;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.input-group {
  margin-bottom: 20px;
}

label {
  display: block;
  margin-bottom: 5px;
  font-weight: bold;
  color: #333;
}

input,
select {
  width: 100%;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
  font-size: 16px;
  box-sizing: border-box;
}

input:focus,
select:focus {
  outline: none;
  border-color: #42b983;
}

.resultado {
  margin-top: 30px;
  padding: 20px;
  background: #fff;
  border-radius: 5px;
  text-align: center;
  border: 2px solid #42b983;
}

.resultado h2 {
  margin: 0 0 10px 0;
  color: #333;
}

.valor-resultado {
  font-size: 32px;
  font-weight: bold;
  color: #42b983;
}
</style>