<script setup>
import Base from './components/Base.vue';
import BaseComponent from "./components/BaseComponent.vue"
</script>

<template>
<h2>ディレクティブを使用（Base.vueでbase.jsも使用）</h2>
<h3>h３　ルート階層</h3>
 <div>
   <h3>h３　1つ下階層</h3>
   <Base class="Base" />
 </div>
<h2>コンポーネントの利用（BaseComponent.vueで各コンポーネントファイルを使用）</h2>
  <BaseComponent />
</template>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
  font-size:60px;
}
h3{
  width:fit-content;
  margin-top:50px;
  margin-right:auto;
  margin-left:auto;
  background-color:rgba(30,155,175,0.5);
}
* /deep/ h3{
  color:red;
}
</style>
