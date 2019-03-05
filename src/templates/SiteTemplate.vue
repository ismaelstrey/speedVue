<template>
  <span id="app">
    <header>
      <NavBar logo="SpeedSul " url="/" cor="#424242 grey darken-3">
        <slot name="links">
          <li>
            <a href="#/">Home</a>
          </li>
          <li>
            <a href="#/login">Entrar</a>
          </li>
          <li>
            <a href="collapsible.html">JavaScript</a>
          </li>
        </slot>
      </NavBar>
    </header>

    <main>
      <div class="container">
        <div class="row">
          <grid-vue tamanho="4">
            <CardMenuVue>
              <slot name="menuesquerdo"/>
            </CardMenuVue>
          </grid-vue>
          <grid-vue tamanho="8">
            <slot name="principal"/>
          </grid-vue>
        </div>
      </div>
    </main>

    <Footer cor="#424242 grey darken-3" logo="SpeedSul" descricao="Teste de descricao" ano="2019">
      <li>
        <a class="grey-text text-lighten-3" href="#!">Link 1</a>
      </li>
      <li>
        <a class="grey-text text-lighten-3" href="#!">Link 2</a>
      </li>
      <li>
        <a class="grey-text text-lighten-3" href="#!">Link 3</a>
      </li>
      <li>
        <a class="grey-text text-lighten-3" href="#!">Link 4</a>
      </li>
    </Footer>
  </span>
</template>

<script>
import NavBar from "@/components/layouts/NavBar";
import Footer from "@/components/layouts/Footer";
import GridVue from "@/components/layouts/GridVue";
import CardMenuVue from "@/components/layouts/CardMenuVue";
export default {
  name: "SiteTemplate",
  components: {
    NavBar,
    Footer,
    GridVue,
    CardMenuVue
  }
};
</script>


