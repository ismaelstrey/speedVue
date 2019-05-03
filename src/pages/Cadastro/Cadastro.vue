<template>
  <LoginTemplate>
    <span slot="menuesquerdo">
      <img
        src="https://www.huddle.com/sites/default/files/image/security-01.png"
        class="responsive-img"
        alt="Background login"
      >
    </span>
    <span slot="principal">
      <h3 class="center">Cadastro</h3>
      <input type="text" placeholder="Nome" autocomplete="username nome" v-model="usuario.name">
      <input type="email" placeholder="E-mail" autocomplete="email e-mail" v-model="usuario.email">
      <input type="password" placeholder="Senha" autocomplete="off" v-model="usuario.password">
      <input
        type="password"
        placeholder="Confirme Sua senha"
        autocomplete="off"
        v-model="usuario.password_confirmation"
      >
      <button class="btn float-left" v-on:click="cadastro()">Enviar</button>
      <router-link class="btn orange" to="/login">Logar</router-link>
    </span>
  </LoginTemplate>
</template>

<script>
import LoginTemplate from "@/templates/LoginTemplate";

export default {
  name: "Cadastro",
  data() {
    return {
      usuario: {
        name: "",
        email: "",
        password: "",
        password_confirmation: ""
      }
    };
  },

  components: {
    LoginTemplate
  },
  methods: {
    cadastro() {
      console.log("Botão cadastro precionado");

      this.$http
        .post(this.$urlAPI + `cadastro`, {
          name: this.usuario.name,
          email: this.usuario.email,
          password: this.usuario.password,
          password_confirmation: this.usuario.password_confirmation
        })
        .then(response => {
          console.log(response);
          if (response.data.status) {
            //  Cadastro realizado com sucesso
            console.log("Cadastro realizado com sucesso");
            this.$store.commit('setUsuario', response.data.usuario);
            sessionStorage.setItem(
              "usuario",
              JSON.stringify(response.data.usuario)
            );
            this.$router.push("/");
          } else if (response.data.status == false && response.data.validacao) {
            console.log("Erros na validação");
            let erros = "";
            for (let erro of Object.values(response.data.erros)) {
              erros += erro + " ";
            }
            alert(erros);
          } else {
            // Erro ao cadatrar usuario
            console.log("Erro ao cadatrar usuario");
            alert("Erro ao cadastrar! Tente mais tarde");
          }
        })
        .catch(e => {
          console.log(e);
          alert("Erro !Tente Novamente mais tarde");
        });
    }
  }
};
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
