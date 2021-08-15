<template>
  <div>
    <Titulo titulo="Times" />
    <hr />
    <table>
      <thead>
        <th>Nome do time</th>
        <th>Jogador 1</th>
        <th>Jogador 2</th>
        <th>Ação</th>
      </thead>
      <tbody>
        <td>
          <input type="text" placeholder="Nome do time" v-model="nomeTime" />
        </td>
        <td><input type="text" placeholder="Jogador 1" v-model="nomeJ1" /></td>
        <td><input type="text" placeholder="Jogador 2" v-model="nomeJ2" /></td>
        <td><button class="btn" @click="adicionarTime()">Inserir</button></td>
      </tbody>
    </table>

    <br />
    <table>
      <thead>
        <th>id</th>
        <th>Nome do time</th>
        <th>Jogador 1</th>
        <th>Jogador 2</th>
        <th>Ação</th>
      </thead>
      <tbody>
        <tr v-for="(time, index) in times" :key="index">
          <td>{{ time.id }}</td>
          <td>{{ time.Nome }}</td>
          <td>{{ time.Jogador1 }}</td>
          <td>{{ time.Jogador2 }}</td>
          <td>
            <button class="btn btn_Danger" @click="removerTime(time)">
              Remover
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import Titulo from "../_shared/Titulo.vue";

export default {
  components: {
    Titulo,
  },
  data() {
    return {
      titulo: "Times de sinuca",
      nomeTime: "",
      nomeJ1: "",
      nomeJ2: "",
      times: [],
    };
  },

  created() {
    this.$http
      .get("http://localhost:3000/times")
      .then((res) => res.json())
      .then((times) => (this.times = times));
  },

  props: {},
  methods: {
    adicionarTime() {
      if (
        this.nomeTime.length == 0 ||
        this.nomeJ1.length == 0 ||
        this.nomeJ2.length == 0
      ) {
        alert("Todos os campos devem ser preenchidos.");
        return;
      }

      let _time = {
        // id: 0,
        Nome: this.nomeTime,
        Jogador1: this.nomeJ1,
        Jogador2: this.nomeJ2,
      };

      // Insere time
      this.$http
        .post("http://localhost:3000/times", _time)
        .then((res) => res.json())
        .then((timeRetornado) => {
          this.times.push(timeRetornado);
        });

      // Limpa console
      console.clear();
      console.log(_time);

      // Limpa campos de inserção
      this.nomeTime = "";
      this.nomeJ1 = "";
      this.nomeJ2 = "";
    },

    removerTime(time) {
      this.$http.delete(`http://localhost:3000/times/${time.id}`).then(() => {
        let indiceTime = this.times.indexOf(time);
        this.times.splice(indiceTime, 1);
      });
    },
  },
};
</script>

<style></style>
