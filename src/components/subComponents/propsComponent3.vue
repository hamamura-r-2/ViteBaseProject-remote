<!-- クラスとID、スタイルを渡すpropsのサンプルコンポーネント -->
<script>
export default {
  inheritAttrs: false,
};
</script>


<script setup>

</script>


<template>
<div :id="$attrs.id">
    div第一要素開始（inheritattrs:falseにより親のクラスは引き継がない）ーーーーーーーーーーーーーーー
    <div class="child" :style="$attrs.style">div第二要素</div>
    <p class="child" :class="$attrs.class" :style="$attrs.style" :id="$attrs.id">p要素</p>
    div第一要素終了ーーーーーーーーーーーーーーー
</div>
</template>


<style>

</style>