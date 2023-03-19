<template>
    <div class="container">
        <div class="content-radiu1">
            <h2 class="title">\ たっだ4問 /</h2>
            <p class="desc">カンタン！30秒で完了！</p>
            <div class="question">
                <div class="q1">Q1</div>
                <div class="q-text">
                    長時間の歩行や立ち仕事で、足がよく
                    だるくなったり痛くなりますか？
                </div>
            </div>
            <AnserRadio :data="data_1" :radioValue="radio1_value" @changefunc="handleChangeVal"/>
        </div>

        <button @click="handleViewData">submit</button>
    </div>
</template>

<script>
import AnserRadio from "./comp/radio"

export default {
    components: {
        AnserRadio
    },
    props: {

    },
    data() {
        return {
            data_1: {
                img: "https://cdn.shopify.com/s/files/1/0532/3063/3157/files/Style2_Q1.png?v=1678987425",
                radio_list1: [
                    {
                        text: "はい",
                        id: 1,
                        value: 1,
                        radio_name: 'radio1'
                    },
                    {
                        text: "いいえ",
                        id: 2,
                        value: 2,
                        radio_name: 'radio1'
                    }
                ],
            },
            radio1_value: undefined,
        }
    },
    methods: {
        handleChangeVal(name, val) {
            this[name] = val
        },
        handleViewData() {
            console.log(this.radio1_value)
        }
    }
}
</script>

<style lang="less" scoped>
.container {
    .content-radiu1 {
        background: #EACCAF;
        overflow: hidden;
        font-family: "Noto Serif JP";
        padding: 0 20px;
        .title {
            font-size: 34px;
            line-height: 49px;
            margin-top: 50px;
            text-align: center;
        }
        .desc {
            font-size: 16px;
            line-height: 23px;
            text-align: center;
        }
        .question {
            margin-top: 29px;
            display: flex;
            justify-content: center;
            align-items: flex-end;
            .q1 {
                font-size: 60px;
                line-height: 60px;
                margin-top: 5px;
            }
            .q-text {
                font-size: 16px;
                line-height: 22px;
                margin-bottom: 5px;
            }
        }
    }
}
</style>