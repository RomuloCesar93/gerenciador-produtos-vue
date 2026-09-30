<script setup>
import { ref } from "vue";
const produtos = ref([
  { id: 1, nome: "Cafeteira", preco: 49.99, quantidade: 10 },
  { id: 2, nome: "Cuscuzeira", preco: 59.99, quantidade: 8 },
  { id: 3, nome: "Panela", preco: 119.99, quantidade: 5 },
  { id: 4, nome: "Tapete", preco: 29.99, quantidade: 9 },
  { id: 5, nome: "Liquidificador", preco: 89.99, quantidade: 7 },
]);

const nome = ref("");
const preco = ref("");
const quantidade = ref("");

function removerProduto(id) {
  produtos.value = produtos.value.filter((produto) => produto.id !== id);
}
function adicionarProduto() {
  const novoProduto = {
    id: Date.now(),
    nome: nome.value,
    preco: Number(preco.value),
    quantidade: Number(quantidade.value),
  };
  produtos.value.push(novoProduto);

  nome.value = "";
  preco.value = "";
  quantidade.value = "";
}
</script>

<template>
  <main>
    <h1>Gerenciador de Produtos!</h1>
    <ul>
      <li v-for="produto in produtos" :key="produto.id">
        {{ produto.id }} - {{ produto.nome }} - R$ {{ produto.preco }} - Qtd
        {{ produto.quantidade }}
        <span class="barato" v-if="produto.preco < 50"> Produto Barato </span>
        <span class="caro" v-else> Produto Caro </span>

        <button @click="removerProduto(produto.id)">Remover</button>
      </li>
    </ul>
    <div class="formulario">
      <input v-model="nome" type="text" placeholder="Nome" />
      <input v-model="preco" type="number" placeholder="Preço" />
      <input v-model="quantidade" type="number" placeholder="Quantidade" />
      <button @click="adicionarProduto">Adicionar</button>
    </div>
  </main>
</template>

<style scoped>
main {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}
h1 {
  text-align: center;
}
ul {
  list-style: none;
  padding: 0;
}
li {
  padding: 15px;
  margin-bottom: 10px;
  border: 1px solid black;
  border-radius: 12px;
  display: flex;
  align-items: center;
  gap: 15px;
}
button {
  padding: 8px 12px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  margin-left: auto;
}
input {
  padding: 10px;
  margin-right: 8px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 6px;
}
.formulario {
  display: flex;
  gap: 20px;
}
.barato {
  color: green;
  font-weight: bold;
}
.caro {
  color: red;
  font-weight: bold;
}
</style>
