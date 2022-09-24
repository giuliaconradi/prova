<template>
  <div>
    <h2>Informe o nome e as respectivas notas</h2>
    <form @submit.prevent="inserir()">
      <input submit="text" v-model="nome" placeholder="Nome" /><br /><br />
      <input type="number" v-model="nota1" placeholder="Primeira Nota" /><br />
      <input type="number" v-model="nota2" placeholder="Segunda Nota" /><br />
      <input
        type="number"
        v-model="nota3"
        placeholder="Terceira Nota"
      /><br /><br />
      <input type="submit" value="Ver Resultado" /><br />
    </form>
    <br />

    <table>
      <tr>
        <th>Nome</th>
        <th>Resultado</th>
      </tr>
      <tr v-for="p in projetos" :key="p.resultado" :class="[p.resultado]">
        <td>{{ p.nome }}</td>

        <td>{{ p.resultado }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nome: "",
      nota1: null,
      nota2: null,
      nota3: null,
      projetos: [
        {
          nome: "",
          resultado: "",
        },
      ],
    };
  },
  methods: {
    inserir() {
      this.projetos.push({
        nome: this.nome,
        resultado: this.calcularmedia(),
      });
    },
    calcularmedia() {
      this.projetos.nota1 = this.nota1;
      this.projetos.nota2 = this.nota2 * 2;
      this.projetos.nota3 = this.nota3 * 3;
      let soma =
        this.projetos.nota1 + this.projetos.nota2 + this.projetos.nota3;
      let media = soma / 6;
      if (media > 7) {
        return "Aprovado";
      } else return "Reprovado";
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.Aprovado {
  background-color: rgb(0, 183, 255);
}
.Reprovado {
  background-color: rgb(250, 11, 11);
}
</style>
