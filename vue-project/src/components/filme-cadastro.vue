<template>
  <div>
    <h1>Cadastro de Filmes</h1>
    <div>
      <input v-model="novoFilme.titulo" placeholder="Título" />
      <input v-model="novoFilme.diretor" placeholder="Diretor" />
      <input v-model="novoFilme.ano" type="number" placeholder="Ano" />
      <button @click="adicionarFilme">Cadastrar Filme</button>
    </div>
    
    <div v-if="filmes.length === 0">Nenhum filme cadastrado.</div>
    <ul>
      <li v-for="(filme, index) in filmes" :key="index">
        {{ filme.titulo }} - {{ filme.diretor }} ({{ filme.ano }})
        <button @click="removerFilme(index)">Deletar</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      novoFilme: {
        titulo: '',
        diretor: '',
        ano: null,
      },
      filmes: [],
    };
  },
  methods: {
    adicionarFilme() {
      if (this.novoFilme.titulo && this.novoFilme.diretor && this.novoFilme.ano) {
        this.filmes.push({ ...this.novoFilme });
        this.limparCampos();
      } else {
        alert('Por favor, preencha todos os campos.');
      }
    },
    removerFilme(index) {
      this.filmes.splice(index, 1);
    },
    limparCampos() {
      this.novoFilme.titulo = '';
      this.novoFilme.diretor = '';
      this.novoFilme.ano = null;
    },
  },
};
</script>