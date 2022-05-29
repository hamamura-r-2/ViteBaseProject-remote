<script setup>
    import { ref } from 'vue';

    const users = ref([]);

    const fetchPost = async () => {
    const res = await fetch('https://jsonplaceholder.typicode.com/users');
    users.value = await res.json();
    };
    fetchPost();
</script>


<template>
    <p style="font-size:20px; font-weight:900;">子から値を渡すslotです。</p>
    <slot name="slot1" message="こんにちは"></slot>
    <slot message="こんばんは" menu="カレー"></slot>
    <p style="font-size:20px; font-weight:900;">v-forで、jsonplaceholderで取得した、10個のオブジェクトからなる配列を子から親へ渡す</p>
    <slot name="json" v-for="user in users" :user="user"></slot>
    <!-- <p style="font-size:20px; font-weight:900;">v-forを使わずに、一つずつ書いても同じ（3つだけ記載）。渡すslotpropsの名前が同じなら、同じ名前のslotタグが複数あっても良い？</p>
    <slot name="json" :user="users[0]"></slot>
    <slot name="json" :user="users[1]"></slot>
    <slot name="json" :user="users[2]"></slot>
    と思ったが、この書き方をすると、次のDynamicの要素が表示されなくなったので、コメントアウトした。
    -->
</template>


<style>

</style>