<script setup>
    import {ref} from "vue";
    const count2 = ref(0);
</script>


<template>
    <div>Dynamicコンポーネント２です。</div>
    <button @click="count2++;">増やす</button>
    <div>{{count2}}</div>
</template>


<style>

</style>