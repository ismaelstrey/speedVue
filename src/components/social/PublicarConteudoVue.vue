<template>
  <div class="row">
    <GridVue class="input-field" tamanho="12">
      <input type="text" v-model="conteudo.titulo">
      <textarea v-if="conteudo.titulo" placeholder="Conteudo" v-model="conteudo.texto" id="conteudoID" class="materialize-textarea"></textarea>
      <input v-if="conteudo.titulo && conteudo.texto" placeholder="Link:"  type="text" v-model="conteudo.link">
      <input v-if="conteudo.titulo && conteudo.texto" placeholder="Url da Imagem" type="text" v-model="conteudo.img">
      <label>O que está acontecendo?</label>
    </GridVue>
    <p v-if="conteudo.texto" class="right-align">
      <button
        @click="addConteudo"
        v-if="conteudo"
        class="btn waves-effect waves-light circle default"
      >
        <i class="material-icons">send</i>
      </button>
    </p>
  </div>
</template>

<script>
import GridVue from "@/components/layouts/GridVue";

export default {
  name: "PublicarConteudoVue",
  props: [],
  data() {
    return {
      conteudo: {
        titulo:'',
        texto:'',
        link:'',
        img:''
      }
    };
  },
  components: {
    GridVue
  },
  methods:{
    addConteudo(){
      console.log(this.conteudo);
    this.$http.post(this.$urlAPI+`conteudo/adicionar`,this.conteudo,{
      headers: { authorization: "Bearer " + this.$store.getters.getToken }
    }).then(response=>{
      if(response.data.status){
        console.log(response.data.conteudos);
      }
    }).catch(e =>{
      console.log(e);
      alert("Erro! Tente mais Tarde");
    })
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
