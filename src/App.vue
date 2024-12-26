<template>
  <div id="app" class="container">
    <h1>Calculadora Aritmética</h1>
    <div class="calculator">
      <input
        type="number"
        v-model.number="numero1"
        placeholder="Digite o primeiro número"
        class="input"
      />
      <select v-model="operacao" class="select">
        <option value="soma">➕ Soma</option>
        <option value="subtracao">➖ Subtração</option>
        <option value="multiplicacao">✖️ Multiplicação</option>
        <option value="divisao">➗ Divisão</option>
      </select>
      <input
        type="number"
        v-model.number="numero2"
        placeholder="Digite o segundo número"
        class="input"
      />
    </div>
    <div class="resultado">
      <h2>Resultado: <span class="resultado-text">{{ resultado }}</span></h2>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numero1: 0,
      numero2: 0,
      operacao: "soma",
    };
  },
  computed: {
    resultado() {
      switch (this.operacao) {
        case "soma":
          return this.numero1 + this.numero2;
        case "subtracao":
          return this.numero1 - this.numero2;
        case "multiplicacao":
          return this.numero1 * this.numero2;
        case "divisao":
          return this.numero2 !== 0
            ? (this.numero1 / this.numero2).toFixed(2)
            : "Erro: Divisão por zero";
        default:
          return "Operação inválida";
      }
    },
  },
};
</script>

<style>
/* Estilo global */
body {
  font-family: 'Arial', sans-serif;
  background-color: #f5f7fa;
  color: #333;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

/* Container principal */
.container {
  background: #ffffff;
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  max-width: 400px;
  width: 100%;
  text-align: center;
}

/* Título */
h1 {
  color: #2c3e50;
  margin-bottom: 20px;
  font-size: 24px;
}

/* Seção da calculadora */
.calculator {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

/* Estilo dos inputs */
.input,
.select {
  padding: 10px 15px;
  font-size: 16px;
  border: 1px solid #dfe6e9;
  border-radius: 8px;
  width: 100%;
  box-sizing: border-box;
}

/* Alteração no foco */
.input:focus,
.select:focus {
  outline: none;
  border-color: #74b9ff;
  box-shadow: 0 0 5px rgba(116, 185, 255, 0.5);
}

/* Resultado */
.resultado {
  margin-top: 20px;
  font-size: 18px;
  font-weight: bold;
}

.resultado-text {
  color: #0984e3;
  font-size: 24px;
}
</style>

