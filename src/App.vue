<template>
  <div id="app">
    <h1>Listagem de Itens VUE.</h1>

    <button @click="view = 'form'">Cadastro</button>
    <button @click="view = 'list'">Listagem</button>

    <div v-if="view === 'form'">
      <h2>Cadastre o item</h2>
      <input v-model="newItem.name" placeholder="Nome" />
      <input v-model="newItem.description" placeholder="Descrição" />
      <button @click="addItem">Adicionar</button>
    </div>

    <div v-if="view === 'list'">
      <h2>Itens Cadastrados</h2>
      <ul>
        <li v-for="(item, index) in items" :key="index">
          {{ item.name }} - {{ item.description }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      view: 'form',
      newItem: { name: '', description: '' },
      items: [],
    };
  },
  methods: {
    addItem() {
      if (this.newItem.name && this.newItem.description) {
        this.items.push({ ...this.newItem });
        this.newItem = { name: '', description: '' };
        this.view = 'list';
      }
    },
  },
};
</script>

<style scoped>
#app {
  text-align: center;
  font-family: Arial, sans-serif;
  margin: 20px;
}

button {
  margin: 10px;
}
</style>
