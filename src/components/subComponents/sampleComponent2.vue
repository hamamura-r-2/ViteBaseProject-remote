<!-- ただの配置用のサンプルコンポーネント２ -->
<script setup>
    import {ref} from "vue";
    const count = ref(1);

</script>



<template>
    <div>コンポーネントのサンプル２</div>
    <button @click="count++">増やす</button>
    {{count}}
</template>



<style>

</style>