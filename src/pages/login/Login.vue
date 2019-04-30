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
      <span>
        <h3 class="center">Login</h3>
        <input type="text" placeholder="E-mail" v-model="usuario.email">
        <input type="password" placeholder="Senha" v-model="usuario.password">
        <button class="btn" v-on:click="login()">Entrar</button>
        <router-link class="btn orange" to="/cadastro">Criar conta</router-link>
      </span>
    </span>
  </LoginTemplate>
</template>

<script>
import LoginTemplate from "@/templates/LoginTemplate";

export default {
  name: "Login",
  data() {
    return {
      usuario: { email: "", password: "" }
    };
  },

  components: {
    LoginTemplate
  },
  methods: {
    login() {
      console.log("ok");

      this.$http
        .post(this.$urlAPI + `login`, {
          email: this.usuario.email,
          password: this.usuario.password
        })
        .then(response => {
          //  console.log(response)
          if (response.data.token) {
            //  Login com sucesso
            console.log("Login Com sucesso");
            sessionStorage.setItem("usuario", JSON.stringify(response.data));
            this.$router.push("/");
          } else if (response.data.status == false) {
            // Login não existe
            console.log("Login não existe");
          } else {
            console.log("Erros na validação");
            let erros = "";
            for (let erro of Object.values(response.data)) {
              erros += erro + " ";
            }
            alert(erros);
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
