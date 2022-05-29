<!-- emitで子から親へ通知を出して親が子に与えるpropsの値を書き換えるコンポーネント -->
<script setup>
    defineProps({
        name:String
    })
   const emitsbox = defineEmits(['changeNameEvent']);
   const changeName = () => {
  emitsbox('changeNameEvent');
};

</script>


<template>
    <div>{{name}}</div>
     <button @click="changeName">通知</button>
</template>


<style>

</style>