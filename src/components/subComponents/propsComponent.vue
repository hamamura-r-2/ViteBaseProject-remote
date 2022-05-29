<!-- 文字列propsのサンプルコンポーネント -->
<script setup>
import { stringifyStyle } from '@vue/shared';


defineProps({
    message: String,
    name: {type:String, default:"親が名付けてくれなかったらこれが表示される"},
    tel:{type:String,required:true}
})

</script>


<template>
    <div style="font-size:20px;font-weight:900;">文字列propsのサンプル</div>
    <div>MESSAGE:　{{message}}</div>
    <div>NAME:　{{name}}</div>
    <div>TEL(親で指定しなければconsoleでエラーになる):　{{tel}}</div>
</template>


<style>

</style>