<template>
    <div class="container">
        <!-- question 1 -->
        <div class="content-radiu1">
            <h2 class="title"><span>\</span> たっだ4問 <span>/</span></h2>
            <p class="desc">カンタン！30秒で完了！</p>
            <div class="question">
                <div class="q1">Q1</div>
                <div class="q-text">
                    長時間の歩行や立ち仕事で、足がよく
                    だるくなったり痛くなりますか？
                </div>
            </div>
            <AnserRadio :data="data_1" :radioValue="radio1_value" :imgsrc="radio1_img" @changefunc="handleChangeVal" attr_name1="radio1_value" attr_name2="radio1_img" padding_left="42px" />
        </div>
        <img class="radio_img" v-show="radio1_img" :src="radio1_img" alt="VIVAIA">

        <!-- question 2 -->
        <div class="content-radiu1" v-if="radio1_value">
            <h2 class="title"><span>\</span> たっだ3問 <span>/</span></h2>
            <p class="desc">カンタン！30秒で完了！</p>
            <div class="question">
                <div class="q1">Q2</div>
                <div class="q-text">
                    長時間の歩行・立ち仕事の後、
                    最も悩む足のトラブルはどれですか？
                </div>
            </div>
            <AnserRadio :data="data_2" :radioValue="radio2_value" :imgsrc="radio2_img" @changefunc="handleChangeVal" attr_name1="radio2_value" attr_name2="radio2_img" padding_left="30px"/>
        </div>
        <img class="radio_img" v-if="radio2_img" :src="radio2_img" alt="VIVAIA">

        <!-- question 3 -->
        <div class="content-radiu1" v-if="radio2_value">
            <h2 class="title"><span>\</span> たっだ2問 <span>/</span></h2>
            <p class="desc">カンタン！30秒で完了！</p>
            <div class="question">
                <div class="q1">Q3</div>
                <div class="q-text">
                    その足のトラブルをどのように
                    解決していますか？
                </div>
            </div>
            <AnserRadio :data="data_3" :radioValue="radio3_value" :imgsrc="radio3_img" @changefunc="handleChangeVal" attr_name1="radio3_value" attr_name2="radio3_img" padding_left="30px"/>
        </div>
        <img class="radio_img" v-if="radio3_img" :src="radio3_img" alt="VIVAIA">

        <!-- question 4 -->
        <div class="content-radiu1" v-if="radio3_value">
            <h2 class="title"><span>\</span> たっだ1問 <span>/</span></h2>
            <p class="desc">限定特典まであと一歩！</p>
            <div class="question">
                <div class="q1">Q4</div>
                <div class="q-text">
                    Aria5°フラットシューズの
                    どこに惹かれましたか？
                </div>
            </div>
            <AnserCheckbox :data="data_4" :checkboxValue="radio4_value" :imgsrc="radio4_img" @changefunc="handleChangeVal" attr_name1="radio4_value" attr_name2="radio4_img" padding_left="20px"/>
        </div>
        <div class="submit" v-if="radio4_value.length">
            <button class="submit-btn" @click="handleViewData">回答完了</button>
        </div>
        <img class="radio_img" v-if="radio4_value.length" :src="radio4_img" alt="VIVAIA">
    </div>
</template>

<script>
import AnserRadio from "./comp/radio"
import AnserCheckbox from "./comp/checkbox.vue"

export default {
    components: {
        AnserRadio,
        AnserCheckbox
    },
    props: {

    },
    data() {
        return {
            data_1: pt_hello_data.data_1,
            radio1_value: pt_hello_data.radio1_value,
            radio1_img: pt_hello_data.radio1_img,
            data_2: pt_hello_data.data_2,
            radio2_value: pt_hello_data.radio2_value,
            radio2_img: pt_hello_data.radio2_img,
            data_3: pt_hello_data.data_3,
            radio3_value: pt_hello_data.radio3_value,
            radio3_img: pt_hello_data.radio3_img,
            data_4: pt_hello_data.data_4,
            radio4_value: pt_hello_data.radio4_value,
            radio4_img: pt_hello_data.radio4_img,
        }
    },
    methods: {
        handleChangeVal(name, val) {
            this[name] = val

        },
        handleViewData() {
            console.log(this.radio4_value)
        }
    }
}
</script>

<style lang="less" scoped>
.container {
    font-size: 0px;
    .content-radiu1 {
        background: #EACCAF;
        overflow: hidden;
        padding-bottom: 50px;
        .title {
            font-size: 34px;
            line-height: 49px;
            margin-top: 50px;
            text-align: center;
            font-family: 'Noto Serif JP';
            font-weight: 600;
        }
        .desc {
            font-size: 16px;
            line-height: 23px;
            text-align: center;
            font-family: 'Noto Serif JP';
            font-weight: 500;
        }
        .question {
            margin-top: 29px;
            display: flex;
            justify-content: center;
            align-items: flex-end;
            padding: 0 12px 12px;
            .q1 {
                font-size: 60px;
                line-height: 60px;
                margin-top: 5px;
                font-family: 'Noto Serif JP';
                font-weight: 700;
            }
            .q-text {
                font-size: 16px;
                line-height: 22px;
                margin-bottom: 5px;
                font-family: 'Noto Serif JP';
                font-weight: 700;
                position: relative;
                top: 10px;
            }
        }
    }
    .radio_img {
        display: inline-block;
        width: 100%;
    }
    .submit {
        text-align: center;
        background: #EACCAF;
        border-radius: 5px;
        .submit-btn {
            font-size: 16px;
            height: 40px;
            line-height: 20px;
            padding: 10px 30px;
            color: #ffffff;
            background: rgba(138, 92, 49, 0.71);;
            border: none;
            display: inline-block;
            margin: 0 auto;
            position: relative;
            top: -20px;
        }
    }
}
</style>