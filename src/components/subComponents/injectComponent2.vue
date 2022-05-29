<script setup>
    import { inject } from 'vue';
    const mine = inject("legacy");
    const changeMind = inject("claim")
</script>


<template>
    <div>孫コンポーネント</div>
    <button @click="changeMind">やっぱり違うのにしたい</button><br>
    もらったものを表示：{{mine}}
</template>


<style>

</style>