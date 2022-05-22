<!-- コンポーネントの例を集めたコンポーネント -->
<script setup>

import sampleComponent1 from "./subComponents/sampleComponent1.vue";
import sampleComponent2 from "./subComponents/sampleComponent2.vue";
import propsComponent from "./subComponents/propsComponent.vue";
import propsComponent2 from "./subComponents/propsComponent2.vue";
import propsComponent3 from "./subComponents/propsComponent3.vue"
import {ref,reactive} from "vue";

let givePresent = ref("親から渡すリアクティブ変数")
const changePresent = () => {
    givePresent.value = "誕生日プレゼント"
}

const givePresent2 = reactive({content:"親から渡すリアクティブオブジェクト"});
const changePresent2 = () => {
    givePresent2.content = "誕生日プレゼントオブジェクト";
}

const parentStyle = "color:red";
</script>


<template>
    <h1>コンポーネントの利用</h1>

    <h3>コンポーネントの配置</h3>
    <sample-component1 />
    <sample-component2 />
    <sample-component2 />

    <h3>propsでの文字列渡し</h3>
    <propsComponent message="親から渡すメッセージ" />
    <propsComponent message="親から渡すメッセージ変更" name="今回は名付けた" tel="telも設定" />

    <h3>propsでの変数や真偽値、数値渡し</h3>
    <propsComponent2 message="これはただの文字列" score="1111+1111" iserror="false" present="givePresent" present2="givePresent2"/>
    <propsComponent2 message="これはただの文字列" :score="1111+1111" :iserror="false" :present="givePresent" :present2="givePresent2"/>
    <div>ーーーーーーーーーーーーーーーーーーーーーーーー</div>
    <div>親から渡した変数を、親コンポーネント中のボタンで変更するためのボタン</div>
    <button @click="changePresent">親が値を誕生日プレゼントに変更</button>
    <div>親から渡した変数オブジェクトを、親コンポーネント中のボタンで変更するためのボタン</div>
    <button @click="changePresent2">親が値を誕生日プレゼントオブジェクトに変更</button>

    <h3>親から子へのクラスとスタイルとID渡し</h3>
    <propsComponent3 class="parent" :style="parentStyle" id="parentId"/>


</template>


<style>
    .parent{
        background-color:blue;
    }
</style>