<template>
    <div class="container">
        <!-- question 1 -->
        <div class="content-radiu1">
            <h2 class="title"><span>\</span> たった4問 <span>/</span></h2>
            <p class="desc">カンタン！30秒で完了！</p>
            <div class="question">
                <div class="q1">Q1</div>
                <div class="q-text">
                    長時間の歩行や立ち仕事で、足がよくだるくなったり痛くなりますか？
                </div>
            </div>
            <AnserRadio :data="data_1" :radioValue="radio1_value" :imgsrc="radio1_img" @changefunc="handleChangeVal" attr_name1="radio1_value" attr_name2="radio1_img" attr_name3="radio1_text" attr_name4="radio1_img_src" padding_left="42px" />
        </div>
        <a v-if="radio1_img_src" :href="radio1_img_src">
            <img class="radio_img" v-show="radio1_img" :src="radio1_img" alt="VIVAIA">
        </a>
        <img v-else class="radio_img" v-show="radio1_img" :src="radio1_img" alt="VIVAIA">

        <!-- question 2 -->
        <div class="content-radiu1" v-if="radio1_value">
            <h2 class="title"><span>\</span> 残り3問 <span>/</span></h2>
            <p class="desc">カンタン！30秒で完了！</p>
            <div class="question">
                <div class="q1">Q2</div>
                <div class="q-text">
                    長時間の歩行・立ち仕事の後、最も悩む足のトラブルはどれですか？
                </div>
            </div>
            <AnserRadio :data="data_2" :radioValue="radio2_value" :imgsrc="radio2_img" @changefunc="handleChangeVal" attr_name1="radio2_value" attr_name2="radio2_img" attr_name3="radio2_text" attr_name4="radio2_img_src" padding_left="30px"/>
        </div>
        <a v-if="radio2_img_src" :href="radio2_img_src">
            <img class="radio_img" v-show="radio2_img" :src="radio2_img" alt="VIVAIA">
        </a>
        <img v-else class="radio_img" v-show="radio2_img" :src="radio2_img" alt="VIVAIA">

        <!-- question 3 -->
        <div class="content-radiu1" v-if="radio2_value">
            <h2 class="title"><span>\</span> 残り2問 <span>/</span></h2>
            <p class="desc">カンタン！30秒で完了！</p>
            <div class="question">
                <div class="q1">Q3</div>
                <div class="q-text">
                    その足のトラブルをどのように解決していますか？
                </div>
            </div>
            <AnserRadio :data="data_3" :radioValue="radio3_value" :imgsrc="radio3_img" @changefunc="handleChangeVal" attr_name1="radio3_value" attr_name2="radio3_img" attr_name3="radio3_text" attr_name4="radio3_img_src" padding_left="30px"/>
        </div>
        <a v-if="radio3_img_src" :href="radio3_img_src">
            <img class="radio_img" v-show="radio3_img" :src="radio3_img" alt="VIVAIA">
        </a>
        <img v-else class="radio_img" v-show="radio3_img" :src="radio3_img" alt="VIVAIA">

        <!-- question 4 -->
        <div class="content-radiu1" v-if="radio3_value">
            <h2 class="title"><span>\</span> 残り1問 <span>/</span></h2>
            <p class="desc">限定特典まであと一歩！</p>
            <div class="question">
                <div class="q1">Q4</div>
                <div class="q-text">
                    Aria5°フラットシューズのどこに惹かれましたか？【複数選択】
                </div>
            </div>
            <AnserCheckbox :data="data_4" :checkboxValue="radio4_value" :imgsrc="radio4_img" @changefunc="handleChangeVal" attr_name1="radio4_value" attr_name2="radio4_text_arr" padding_left="20px" :checkboxText="radio4_text_arr" />
        </div>
        <div class="submit" v-if="radio4_value.length">
            <button class="submit-btn" @click="handleViewData">回答完了</button>
        </div>
        
        <a :href="radio4_img_skip">
            <img class="radio_img" v-if="finished" :src="radio4_img" alt="VIVAIA">
        </a>
        <a :href="radio4_img2_skip">
            <img class="radio_img" v-if="finished" :src="radio4_img2" alt="VIVAIA">
        </a>
        <div class="radio_div_comp" v-if="finished">
            <img class="radio_img" :src="radio4_img3" alt="VIVAIA">
            <div class="radio_div_container">
                <a class="radio_div" :href="radio4_img3_skip1"></a>
                <a class="radio_div" :href="radio4_img3_skip2"></a>
                <a class="radio_div" :href="radio4_img3_skip3"></a>
            </div>
        </div>
    </div>
</template>

<script>
import AnserRadio from "./comp/radio"
import AnserCheckbox from "./comp/checkbox.vue"
import { nanoid } from 'nanoid'

export default {
    components: {
        AnserRadio,
        AnserCheckbox
    },
    props: {
        changeloading: {
            type: Function
        }
    },
    data() {
        return {
            formId: pt_hello_data.formId,
            uid: "",
            // 1
            data_1: pt_hello_data.data_1,
            radio1_value: pt_hello_data.radio1_value,
            radio1_text: pt_hello_data.radio1_text,
            radio1_img: pt_hello_data.radio1_img,
            radio1_img_src: "",
            // 2
            data_2: pt_hello_data.data_2,
            radio2_value: pt_hello_data.radio2_value,
            radio2_text: pt_hello_data.radio2_text,
            radio2_img: pt_hello_data.radio2_img,
            radio2_img_src: "",
            // 3
            data_3: pt_hello_data.data_3,
            radio3_value: pt_hello_data.radio3_value,
            radio3_text: pt_hello_data.radio3_text,
            radio3_img: pt_hello_data.radio3_img,
            radio3_img_src: "",
            // 4
            data_4: pt_hello_data.data_4,
            radio4_value: pt_hello_data.radio4_value,
            radio4_text_arr: [],
            radio4_img: pt_hello_data.radio4_img,
            radio4_img_skip: pt_hello_data.radio4_img_skip,
            radio4_img2: pt_hello_data.radio4_img2,
            radio4_img2_skip: pt_hello_data.radio4_img2_skip,
            radio4_img3: pt_hello_data.radio4_img3,
            radio4_img3_skip1: pt_hello_data.radio4_img3_skip1,
            radio4_img3_skip2: pt_hello_data.radio4_img3_skip2,
            radio4_img3_skip3: pt_hello_data.radio4_img3_skip3,
            finished: false,
        }
    },
    computed: {
        listenChange () {
            const { radio1_value, radio2_value, radio3_value } = this
            return { radio1_value, radio2_value, radio3_value }
        }
    },  
    watch: {
        radio1_value(newval, oldval) {
            if (newval && oldval === undefined) {
                const scroll_t = window.scrollY
                setTimeout(() => {
                    window.scrollTo(0, scroll_t + 500)
                })
            }
        },
        radio2_value(newval, oldval) {
            if (newval && oldval === undefined) {
                const scroll_t = window.scrollY
                setTimeout(() => {
                    window.scrollTo(0, scroll_t + 500)
                })
            }
        },
        radio3_value(newval, oldval) {
            if (newval && oldval === undefined) {
                const scroll_t = window.scrollY
                setTimeout(() => {
                    window.scrollTo(0, scroll_t + 500)
                })
            }
        },
    },
    mounted() {
        this.uid = nanoid(24)
    },
    methods: {
        handleChangeVal(name, val) {
            this[name] = val
        },
        async handleViewData() {
            this.changeloading(true)
            const params = {
                formId: this.formId,
                uid: this.uid,
                timestamp: Date.now(),
                data: {
                    feetpain_yes_no: this.radio1_text,
                    feetpain_detail: this.radio2_text,
                    feetpain_solution: this.radio3_text,
                    selling_point: JSON.parse(JSON.stringify(this.radio4_text_arr)).join(",")
                }
            }
            try {
                const res = await fetch("https://ecagent.ptengine.com/api/form", {
                    method: "POST",
                    headers: {
                        "Content-Type": "application/json"
                    },
                    body: JSON.stringify(params)
                })
                if (res.ok === true) {
                    this.finished = true
                    this.changeloading(false)
                    const scroll_t = window.scrollY
                    setTimeout(() => {
                        window.scrollTo(0, scroll_t + 500)
                    })
                } else {
                    this.changeloading(false)
                    alert("error")
                }
            } catch (error) {
                this.changeloading(false)
                throw new Error(error)
            }
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
    .radio_div_comp {
        width: 100%;
        height: 297px;
        position: relative;
        .radio_div_container {
            width: 100%;
            height: 100%;
            position: absolute;
            top: 0px;
            .radio_div {
                display: inline-block;
                width: 33%;
                height: 100%;
            }
        }
    }
    .submit {
        text-align: center;
        background: #EACCAF;
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
            border-radius: 5px;
        }
    }
}
</style>