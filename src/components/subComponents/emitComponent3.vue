<script setup>
// emitComponentは、
//2が親への通知をボタンで分けたもので、propsを変数に代入している→バリデーションも追加
//3が親への通知を入力と同時に行うもので、propsを変数に代入していない
//4が親への通知を入力と同時に行うもので、propsを変数に代入している（v-modelで簡潔）

import {ref} from "vue";

const props = defineProps({
    name:String
})
    const emit = defineEmits(['inputNotification'])

    const aa = () => {
        console.log(props.name);
        console.log("inputNameは定義していない");
    }
</script>


<template>
props.name(最初に親からもらう値)：{{props.name}}<br>
子自身による入力値をバインドした値：定義していない<br>

    <input type="text" :value="props.name" @input="$emit('inputNotification',$event.target.value)">
    <button @click="aa">consoleに出力</button>
</template>



<style>

</style>