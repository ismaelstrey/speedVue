<template>
    <span>
        <div v-if="image" class="card-image">
            <img :src="image">
            <span class="card-title">{{titulo}}</span>
        </div>
        <div  v-if="conteudo" class="card-content">
            <p>{{conteudo}}</p>
        </div>
    </span>         
</template>

<script>

export default {
  name: 'CardDetalheVue', 
  props:['image','titulo', 'conteudo'],
  data () {
    return {
     
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
