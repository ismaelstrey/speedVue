<template>
<div class="row">
  <div class="col s12 m6">
    <div class="card blue-grey darken-1">
      <div class="card-content white-text">
        <span class="card-title">HelloWorld</span>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quae illo qui quisquam magnam, aliquid atque eos corporis neque earum beatae debitis facilis laudantium placeat libero cupiditate iure error fuga maiores.</p>
      </div>
      <div class="card-action">
        <a href="#">This is a link</a>
        <a href="#">This is a link</a>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
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
