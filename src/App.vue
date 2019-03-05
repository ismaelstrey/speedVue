<template>
  <span id="app">
 <header> <NavBar logo = "SpeedSul " url = "#" cor="#424242 grey darken-3"/></header>
 

<main>
  <div class="container">
     <div class="row">
     
      <grid-vue tamanho ='4'>

     <CardMenuVue>
           <div class="row valign-wrapper">
            <grid-vue tamanho ='4'>
              <img src="http://archives.materializecss.com/0.100.2/images/yuna.jpg" alt="" class="circle responsive-img"> <!-- notice the "circle" class -->
            </grid-vue>
            <grid-vue tamanho ='8'>
              <span class="black-text">
                <h5>Silvia J.</h5>
                 Add the "circle" class to it to make it appear circular.
              </span>
            </grid-vue>
          </div>
     </CardMenuVue>
      </grid-vue>
      <grid-vue tamanho ='8'><router-view/></grid-vue>
 
    </div>
  </div> 
   
</main>
      
  <Footer cor="#424242 grey darken-3" logo = "SpeedSul" descricao = "Teste de descricao" ano = '2019'>
        <li><a class="grey-text text-lighten-3" href="#!">Link 1</a></li>
        <li><a class="grey-text text-lighten-3" href="#!">Link 2</a></li>
        <li><a class="grey-text text-lighten-3" href="#!">Link 3</a></li>
        <li><a class="grey-text text-lighten-3" href="#!">Link 4</a></li>
  </Footer>
  </span>
</template>

<script>
import NavBar from '@/components/layouts/NavBar'
import Footer from '@/components/layouts/Footer'
import GridVue from '@/components/layouts/GridVue'
import CardMenuVue from '@/components/layouts/CardMenuVue'
export default {
  name: 'app',
  components: {
    NavBar, Footer, GridVue, CardMenuVue
  }
}
</script>


