<!-- コンポーネントの例を集めたコンポーネント -->
<!-- https://reffect.co.jp/vue/vue-js-components#reactive　より -->
<script setup>

import sampleComponent1 from "./subComponents/sampleComponent1.vue";
import sampleComponent2 from "./subComponents/sampleComponent2.vue";
import propsComponent from "./subComponents/propsComponent.vue";
import propsComponent2 from "./subComponents/propsComponent2.vue";
import propsComponent3 from "./subComponents/propsComponent3.vue";
import emitComponent from "./subComponents/emitComponent.vue";
import emitComponent2 from "./subComponents/emitComponent2.vue";
import emitComponent3 from "./subComponents/emitComponent3.vue";
import emitComponent4 from "./subComponents/emitComponent4.vue";
import inputComponent from "./subComponents/inputComponent.vue";
import slotComponent from "./subComponents/slotComponent.vue";
import slotComponent2 from "./subComponents/slotComponent2.vue";
import dynamicComponent1 from "./subComponents/dynamicComponent1.vue";
import dynamicComponent2 from "./subComponents/dynamicComponent2.vue";
import injectComponent from "./subComponents/injectComponent.vue";
import {ref,reactive,computed,provide} from "vue";


let givePresent = ref("親から渡すリアクティブ変数")
const changePresent = () => {
    givePresent.value = "誕生日プレゼント"
}

const givePresent2 = reactive({content:"親から渡すリアクティブオブジェクト"});
const changePresent2 = () => {
    givePresent2.content = "誕生日プレゼントオブジェクト";
}

const parentStyle = "color:red";

const giveName = ref("親から渡された初期Name");
const parentChangeName = () => {
    giveName.value = "子に言われて親が変えたName";
    console.log("通知来た");
}

const giveInputName = ref("親から渡すinput初期表示Name")
const giveNameAsItIs = (recieveName) => {
    giveInputName.value = recieveName;
    console.log("通知来た");
}

const name = ref("初期氏名");
const address = ref("初期住所");
const tel = ref("初期電話番号");
const email = ref("初期メールアドレス");

// v-ifでの表示切り替え用
const dynamic = ref("");
// is属性でのDynamic表示切り替え用
const dynamic2 = ref("");
const tabs = {
    dynamicKey1:dynamicComponent1,
    dynamicKey2:dynamicComponent2
}
const tab = computed(() => {return tabs[dynamic2.value]});

// いろいろテスト
const bbb = ref(dynamic2.value);
const ccc = computed(() => dynamic2.value);
const aaaa = ()=> {
    console.log(dynamic2.value);
    console.log(tab);
}

const variableLegacy = ref("provide/injectで孫へ渡す");
const changeLegacy = () => {
    variableLegacy.value = "やっぱり孫にあげるのはこっちになる（祖父からもらったメソッドで孫が実施）";
}
provide("legacy",variableLegacy);
provide("claim",changeLegacy);
</script>





<template>
    <h1>コンポーネントの利用（BaseComponent.vueで各コンポーネントファイルを使用）</h1>

    <h3>コンポーネントの配置sample-component1,sample-component2</h3>
    <sample-component1 />
    <sample-component2 />
    <sample-component2 />


    <h3>propsでの文字列渡しpropsComponent</h3>
    <propsComponent message="親から渡すメッセージ" />
    <propsComponent message="親から渡すメッセージ変更" name="今回は名付けた" tel="telも設定" />

    <h3>propsでの変数や真偽値、数値渡しpropsComponent2</h3>
    <propsComponent2 message="これはただの文字列" score="1111+1111" iserror="false" present="givePresent" present2="givePresent2"/>
    <propsComponent2 message="これはただの文字列" :score="1111+1111" :iserror="false" :present="givePresent" :present2="givePresent2"/>
    <div>ーーーーーーーーーーーーーーーーーーーーーーーー</div>
    <div>親から渡した変数を、親コンポーネント中のボタンで変更するためのボタン</div>
    <button @click="changePresent">親が値を誕生日プレゼントに変更</button>
    <div>親から渡した変数オブジェクトを、親コンポーネント中のボタンで変更するためのボタン</div>
    <button @click="changePresent2">親が値を誕生日プレゼントオブジェクトに変更</button>

    <h3>親から子へのクラスとスタイルとID渡しpropsComponent3</h3>
    <propsComponent3 class="parent" :style="parentStyle" id="parentId"/>


    <h3>emitによる子から親への通知emitComponent</h3>
    <emitComponent :name="giveName" @changeNameEvent="parentChangeName"/>

    <h3>input要素の入力値を子から親へ渡し、親はそれを子に与える(propsは変数に代入し、通知は別のボタンクリックで実施)emitComponent2</h3>
    <emitComponent2 @inputNotification="giveNameAsItIs" :name="giveInputName"/>
    <div>ここから下は親の領域</div>子からもらうと変わる値：{{giveInputName}}

    <h3>input要素の入力値を子から親へ渡し、親はそれを子に与える(propsは変数に代入せずに利用)emitComponent3</h3>
    <emitComponent3 @inputNotification="giveNameAsItIs" :name="giveInputName"/>
    <div>ここから下は親の領域</div>子からもらうと変わる値：{{giveInputName}}

    <h3>input要素の入力値を子から親へ渡し、親はそれを子に与える(propsは変数に代入し、通知もinputイベントで実施)emitComponent4</h3>
    <emitComponent4 @inputNotification="giveNameAsItIs" :name="giveInputName"/>
    <div>ここから下は親の領域</div>子からもらうと変わる値：{{giveInputName}}


    <h3>inputのコンポーネントinputComponent</h3>
    名前：{{name}}<br>
    住所：{{address}}<br>
    電話番号：{{tel}}<br>
    メール：{{email}}<br>
    <inputComponent :modelValue="name" @notification="name = $event"/>
    <inputComponent :modelValue="address" @notification="address = $event"/>
    <inputComponent :modelValue="tel" @notification="tel = $event"/>
    <inputComponent :modelValue="email" @notification="email = $event"/>
<!-- ↑でv-modelが使える？？？？？？反映されなかった -->

    <h3>slot利用のコンポーネント（複数slot）</h3>
    <slotComponent>
        <div>
            親からdefaultスロットに入れる値(これはtemplateタグで囲まないが、囲んでv-slot:defaultにしてもよい)
            <ul>
                <li>適当にリストタグもいれてみた１</li>
                <li>適当にリストタグもいれてみた２</li>
                <li>適当にリストタグもいれてみた３</li>
            </ul>
        </div>
        <template v-slot:slot1>
            <span style="color:red;">親がslot1に入れる文章(propsと違いhtmlタグごといれられる)</span>
        </template>
        <template v-slot:slot2 style="font-size:30px;"></template>
    </slotComponent>

    <h3>slot利用のコンポーネント（slotprops）</h3>
 <slotComponent2>
        <!-- v-slotは#でも可能 -->
        <template #slot1="recieve1">
            <p>まとめて代入すると、オブジェクトとなる。</p>
            {{recieve1}}<br>
            {{recieve1.message}}<br>
        </template>
        <template #default="{message,menu}">
            <p>こちらは分割代入</p>
            {{message}}<br>
            {{menu}}<br>
        </template>

        <template v-slot:json="{user}">
            <p>子から配列をもらっているので、親で書いたこの文章は繰り返される</p>
            <li>{{user.name}}</li>
        </template>
    </slotComponent2>

    <h3>Dynamicコンポーネントをv-ifでやると</h3>
    <button @click="dynamic='dynamicComponent1'">1に切り替え</button>
    <button @click="dynamic='dynamicComponent2'">2に切り替え</button>
    <keep-alive>
        <dynamicComponent1 v-if="dynamic=='dynamicComponent1'"></dynamicComponent1>
        <dynamicComponent2 v-else-if="dynamic=='dynamicComponent2'"></dynamicComponent2>
        <div v-else>コンポーネントが選択されていません。</div>
    </keep-alive>

    <h3>Dynamicコンポーネントをis属性で行う</h3>
    <button @click="dynamic2='dynamicKey1'">1に切り替え</button>
    <button @click="dynamic2='dynamicKey2'">2に切り替え</button>
    <keep-alive>
        <component v-bind:is="tab"></component>
    </keep-alive>
    <div>

    <button @click="aaaa">チェック</button>（dynamic2の値とtabの中身をコンソール表示）<br>
        dynamic2:{{dynamic2}}<br>
        bbb(refでdynamic2の値が再代入されるか):{{bbb}}<br>
        ccc(computedでdynamic2の値が再代入されるか):{{ccc}}<br>
    </div>


    <h3>provide/injectの利用</h3>
    <input type="text" @input="variableLegacy = $event.target.value">
    <div>祖父での表示：{{variableLegacy}}</div>
    <injectComponent></injectComponent>

<!-- イベント通知は@で行う！！！！！バインドではない！ -->
</template>


<style>
    .parent{
        background-color:blue;
    }
</style>