<template>
  <div id="">
    <h1 v-text="title"></h1>
    <form @submit.prevent="onSubmit()">
      <input type="text" placeholder="Informe o CEP" v-model="cep" />
      <button type="submit">Buscar CEP</button>
    </form>

    <div v-if="loader">
      <img src="../assets/preloader.gif" />
    </div>
    <div v-if="erro !== null">
      {{ erro }}
    </div>

    <div v-show="sucesso === true">
      <p><b>Logradouro: </b>{{ address.logradouro }}</p>
      <p><b>Bairro: </b>{{ address.bairro }}</p>
      <p><b>Cidade: </b>{{ address.localidade }}</p>
      <p><b>Estado: </b>{{ address.uf }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "Buscar CEP com API VIACEP",
      cep: null,
      address: "",
      loader: false,
      erro: "",
      sucesso: false
    };
  },
  methods: {
    onSubmit() {
      this.reset();
      this.loader = true;
      this.$http
        .get(`https://viacep.com.br/ws/${this.cep}/json/`)
        .then(response => {
          console.log(response);
          this.erro = null;
          this.address = response.body;
          this.sucesso = true;
        })
        .catch(error => {
          if (this.cep === null || this.cep === "")
            this.erro = "Informe um CEP.";
          else this.erro = "Cep Inválido !";
        })
        .finally(() => {
          this.loader = false;
        });
    },
    reset() {
      this.address = {};
      this.erro = "";
      this.sucesso = false;
    }
  }
};
</script>
