<script setup>
    defineProps({
        modelValue:String
    })
const emit = defineEmits(['notification'])
</script>


<template>
{{modelValue}}：
    <input
        type="text"
        :value="modelValue"
        @input="$emit('notification',$event.target.value)"
        style="border-radius:5px;padding:10px 20px;"
    >
</template>


<style>

</style>