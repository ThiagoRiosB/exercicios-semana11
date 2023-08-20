<template>
  <div class="card">
    <button @click="$emit('favoritar', id)">Favoritar</button>
    <span v-if="favorito">Favorito</span>
    <img :width="120" src="https://img.freepik.com/icones-gratis/medicamento_318-820421.jpg?q=10&h=200" alt="img medicamento">
    <span>Nome: {{ nome }}</span>
    <span>Laboratório: {{ laboratorio }}</span>
    <span>Preço: {{ preco }}</span>
  </div>

</template>

<script>
export default {
  props: ['nome', 'laboratorio', 'preco', 'favorito', 'id']
}
</script>

<style scoped>
.card {
  display: flex;
  flex-direction: column;
  width: calc(100%/4 - 2em);
  background-color: #c4c4c4;
  margin: 1em;
}
</style>