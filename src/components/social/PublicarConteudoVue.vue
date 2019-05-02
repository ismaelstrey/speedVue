<template>
  <div class="row">
    <GridVue class="input-field" tamanho="12">
      <textarea v-model="conteudo" id="conteudoID" class="materialize-textarea"></textarea>
      <label v-if="!conteudo">O quê está acontecendo?</label>
    </GridVue>
    <p>
      <GridVue
        v-if="conteudo"
        class="btn-floating waves-effect waves-light red col s"
        tamanho="1 offset-s11"
      >
        <i class="material-icons">send</i>
      </GridVue>
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
      conteudo: ""
    };
  },
  components: {
    GridVue
  },
  methods:{
    addConteudo(){
      console.log("ok");
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
