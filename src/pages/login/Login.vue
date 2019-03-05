<template>
  <LoginTemplate>
    <span slot="menuesquerdo">
      <img
        src="https://www.huddle.com/sites/default/files/image/security-01.png"
        class="responsive-img"
        alt="Bacground login"
      >
    </span>
    
    <span slot="principal">
      <h3 class="center">Login</h3>
      <input id="icon_prefix" type="text" placeholder="E-mail" class="validate">
      <input id="icon_telephone" type="text" class="validate">
      <button class="btn float-left">Entrar</button>
    </span>
  </LoginTemplate>
</template>

<script>
import LoginTemplate from "@/templates/LoginTemplate";
import CardConteudoVue from "@/components/social/CardConteudoVue";
import CardDetalheVue from "@/components/social/CardDetalheVue";
import PublicarConteudoVue from "@/components/social/PublicarConteudoVue";

export default {
  name: "Login",
  data() {
    return {
      msg: "Welcome to Your Vue.js App"
    };
  },

  components: {
    LoginTemplate,
    CardConteudoVue,
    CardDetalheVue,
    PublicarConteudoVue
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
