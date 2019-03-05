<template>
<div class="row">
              <div class="card">
                    <div class="card-content">
                      <div class="row valign-wrapper">
                    <GridVue tamanho ='1'>
                      <img :src="perfil" :alt="nome" class="circle responsive-img"> <!-- notice the "circle" class -->
                    </GridVue>
                    <GridVue tamanho ='11'>
                      <span class="black-text">
                        <strong>{{nome}}</strong>
                        <span class="right">
                          <i class="material-icons tiny grey-text">av_timer</i>
                          {{data}}
                        </span>
                        
                      </span>
                    </GridVue>
                  </div>
                  <slot/>
                </div>
              <div class="card-action">
                <i class="material-icons red-text">favorite_border</i>
                  <i class="material-icons blue-text">insert_comment</i>
              </div>
          </div>
</div>
</template>

<script>
import GridVue from '@/components/layouts/GridVue'
export default {
  name: 'CardConteudoVue',
   components: {
   GridVue
  },
  props:['perfil','nome', 'data'],
  data () {
    return {
     
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
