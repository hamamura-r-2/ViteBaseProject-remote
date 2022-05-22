<!-- 変数と数値、真偽値propsのサンプルコンポーネント -->
<script setup>
    defineProps({
        message:String,
        score:Number,
        iserror:Boolean,
        present:String,
        present2:Object
    })
    const changePresent = () => {
        present = "子が自分で選ぶ誕生日プレゼント"
    }
    const changePresent2 = () => {
    present2.content = "子が自分で選ぶ誕生日プレゼント"
}
</script>


<template>
    <div style="font-size:20px;font-weight:900;">変数と数値、真偽値propsのサンプル</div>
    <div>MESSAGE:　{{message}}</div>
    <div>TEL(数値扱いなら演算される):　{{score}}</div>
    <div>
        iserror(真偽値扱いならこの先が表示される):　
        <span v-if="iserror">真なら表示される文字</span>
        <span v-else>偽なら表示される文字</span>
    </div>
    <div style="color:red">変数(プレゼント文字列)：　{{present}}</div>
    <div>子コンポーネント中のプレゼント変更ボタン(エラーになる)</div>
    <button @click="changePresent">自分でプレゼントを選ぶ(できない)</button>
    <div style="color:red">変数(プレゼントオブジェクト)：　
    <span v-if="present2.content==null">親が指定しない場合の初期表示</span>{{present2.content}}</div>
    <button @click="changePresent2">自分でプレゼントオブジェクトを選ぶ(できない)</button>
</template>


<style>

</style>