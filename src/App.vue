<template>

  <div id="app">
    <header class="wunder-header">
      <h1 class="wunder-header-title">今天</h1>
    </header>
    <todo></todo>
    
  </div>
</template>

<script>
import todo from './components/todo'

export default {
  components: {
    todo
  }
}
</script>

<style>
html {
  height: 100%;
  font-family: "Lato","Microsoft Yahei","微软雅黑","STXihei","Meiryo UI","Meiryo","メイリオ","ＭＳ Ｐゴシック","MS PGothic","Hiragino Kaku Gothic Pro","Arial Unicode MS","Helvetica Neue","Helvetica","Arial",sans-serif;
}

body {
  margin: 0;
  padding: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}

header.wunder-header {
  background-color: #668964;
}

.wunder-header .wunder-header-title {
    margin: 0;
    padding: 10px 14px;
    font-size: 20px;
    color: #fff;
    text-align: left;
}

#app {
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  color: #2c3e50;
  /*margin-top: -100px;*/
  font-family: Source Sans Pro, Helvetica, sans-serif;
  text-align: center;
  background-image: url(./assets/bg.jpg);
  background-position: center;
  background-size: cover; 
}

#app a {
  color: #42b983;
  text-decoration: none;
}

</style>
