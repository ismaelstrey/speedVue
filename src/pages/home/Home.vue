<template>
  <SiteTemplate>
    <span slot="menuesquerdo">
      <div class="row valign-wrapper">
        <grid-vue tamanho="4">
          <span v-if="usuario.image">
             <img
            :src="usuario.image"
            :alt="usuario.name"
            class="circle responsive-img"
          >
          </span>
         
          <!-- notice the "circle" class -->
        </grid-vue>
        <grid-vue tamanho="8">
          <span class="black-text">
            <h5 v-if="usuario.name">{{usuario.name}}</h5>
          </span>
        </grid-vue>
      </div>
    </span>
    <span slot="principal">
      <PublicarConteudoVue/>
      <CardConteudoVue
        perfil="http://archives.materializecss.com/0.100.2/images/yuna.jpg"
        nome="Beatriz"
        data="27/05/2018 12:35"
      >
        <CardDetalheVue
          image="http://archives.materializecss.com/0.100.2/images/sample-1.jpg"
          titulo="Paisagem"
          conteudo="E ai com frio!! Ja penssoum um banho nesse rio"
        />
      </CardConteudoVue>
    </span>
  </SiteTemplate>
</template>

<script>
import SiteTemplate from "@/templates/SiteTemplate";
import CardConteudoVue from "@/components/social/CardConteudoVue";
import CardDetalheVue from "@/components/social/CardDetalheVue";
import PublicarConteudoVue from "@/components/social/PublicarConteudoVue";
import GridVue from "@/components/layouts/GridVue";

export default {
  name: "Home",
  data() {
    return {
      msg: "Welcome to Your Vue.js App"
    };
  },created() {
    let usuarioAux = sessionStorage.getItem("usuario");
    if (usuarioAux) {
      this.usuario = JSON.parse(usuarioAux);  
    }else{
      this.$router.push('/login')
    }
  },

  components: {
    SiteTemplate,
    CardConteudoVue,
    CardDetalheVue,
    GridVue,
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
