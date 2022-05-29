<script setup>
    import {ref} from "vue";
    const count1 = ref(0);
</script>


<template>
    <div>Dynamicコンポーネント１です。</div>
    <button @click="count1++;">増やす</button>
    <div>{{count1}}</div>
</template>


<style>

</style>