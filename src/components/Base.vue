<!-- ディレクティブの例を集めたコンポーネント -->

<script setup>
    // インポート
        // リアクティブ化のインポート
        import {ref,reactive} from "vue"
        // v-forの元データをjsファイルよりインポート
        import {students,iserror} from "../data/base"
    // ディレクティブ
        // v-text,v-html
        const message = "<p>これはv-thmlのpタグ</p>"
        // v-model
        const model = ref("input内の初期表示");
        const fixModel = (event) => {
            model.value = event.target.value
        }
        const clicked = () => {
            console.log(typeof model.value)
        }
        // classのバインドとボタン表記の切り替え
        let isBig = ref(false);
        const letterSizeChange = () => {
            isBig.value = !isBig.value;
            }
        const buttonTextChange = (event) => {
            if (event.target.innerText == "サイズを大きくする") {
                event.target.innerText = "サイズを戻す"
            }else{
                event.target.innerText = "サイズを大きくする"
            }
        }

</script>


<template>
    <h1>ディレクティブを使用</h1>

    <h3>v-thmlで表示</h3>
    <div v-html="message"></div>
    <h3>v-textで表示</h3>
    <div v-text="message"></div>

    <h3>v-for:個別でマスタッシュによる表示</h3>
    <div v-for="student in students" v-bind:key="student.id">
        ID:{{student.ID}}<br>
        NAME:{{student.NAME}}<br>
        BLOOD:{{student.BLOOD}}
    </div>
    <h3>v-for:入れ子にして表示</h3>
    <div v-for="student in students" v-bind:key="student.id">
        <div v-for="(value,name) in student" v-bind:key="value">
        {{name}}：{{value}}
        </div>
    </div>

    <h3>v-if,v-show</h3>
    <div v-if="iserror">v-ifエラーです</div>
    <div v-else>v-ifエラーがある場合はここに表示されます(今はない)</div>
    <div v-show="!iserror">v-showエラーがある場合はここに表示されます(今はない</div>

    <h3>v-modelの機能</h3>
    イベントを引数とするメソッドを使用<input type="text" v-bind:value="model" v-on:input="fixModel($event)"><br>
    イベントタグの中で処理<input type="text" :value="model" @input="model = $event.target.value"><br>
    v-modelを使用<input type="text" v-model="model"><br>
    ここに表示「{{model}}」<br>
    lazyで反映を遅延させる
    <input type="text" v-model.lazy="model"><br>
    trimで前後の空白を除く
    <input type="text" v-model.trim="model"><br>
    numberで数値に変換（本来jsは文字列扱い。先頭半角数値の場合のみ）
    <input type="text" v-model.number="model"><button @click="clicked">入力値の型判定ボタン</button>

    <h3>calssのバインド</h3>
    <button @click="letterSizeChange($event),buttonTextChange($event)">サイズを大きくする</button>
    <div :class="{big:isBig}">クラス適用対象文字列</div>

</template>



<style>
    .big{
        font-size:30px;
    }
</style>