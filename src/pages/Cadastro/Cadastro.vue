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
          <input type="text" placeholder="E-mail">
          <input type="password" placeholder="Senha">
          <input type="password" placeholder="Confirme Sua senha">
          <input type="text" placeholder="Nome">
          <input type="text" placeholder="E-mail">
          <button class="btn float-left">Enviar </button>
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
      
    };
  },

  components: {
    LoginTemplate
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
