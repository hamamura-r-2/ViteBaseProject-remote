<script setup>
import Base from './components/Base.vue';
import BaseComponent from "./components/BaseComponent.vue"
</script>

<template>
  <Base />
  <BaseComponent />
</template>

<style>
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
</style>
