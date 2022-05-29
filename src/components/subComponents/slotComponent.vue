<script setup>

</script>


<template>
  <p>親コンポーネントからslotに渡す文章は「<slot name="slot1"></slot>」に入ります。（あれば）</p>
  <p>
      親から渡されるslotがない場合は、「<slot name="slot2">
          <span style="font-size:20px;">これは子がslotに自分でいれた文章(propsと違いhtmlタグごといれられる)</span>
      </slot>」に子自身で設定した文章が表示されます。
  </p>
  <p>
      このslotにはnameをつけていないため、親の方ではdefaultとして指定する。slot→「<slot name="default">
          子で指定していても、親が指定すればそっちが優先される
      </slot>」
  </p>
</template>


<style>

</style>