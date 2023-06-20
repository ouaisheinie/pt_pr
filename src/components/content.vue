<template>
    <div class="container">
        <!-- question 1 -->
        <div id="question-1" class="content-radiu1" :style="{ background: `url(${data_1.bg_img}) no-repeat`}">
            <h2 class="title">たった4問！</h2>
            <p class="desc">カンタン！30秒で完了！</p>
            <Progress :num="1"/>
            <AnserRadio :data="data_1" :radioValue="radio1_value" :imgsrc="radio1_img" @changefunc="handleChangeVal" attr_name1="radio1_value" attr_name2="radio1_img" attr_name3="radio1_text" attr_name4="radio1_img_src" padding_left="20px" question_text="Q1. 長時間の歩行や立ち仕事で、足がよくだるくなったり痛くなりますか？"/>
        </div>
        <a v-if="radio1_img_src" :href="radio1_img_src">
            <img class="radio_img" v-show="radio1_img" :src="radio1_img" alt="VIVAIA">
        </a>
        <img v-else class="radio_img" v-show="radio1_img" :src="radio1_img" alt="VIVAIA">

        <!-- question 2 -->
        <div class="content-radiu1" v-if="radio1_value" :style="{ background: `url(${data_1.bg_img}) no-repeat`}">
            <h2 class="title"><span>\</span> たった3問 <span>/</span></h2>
            <p class="desc">カンタン！30秒で完了！</p>
            <Progress :num="2"/>
            <AnserRadio :data="data_2" :radioValue="radio2_value" :imgsrc="radio2_img" @changefunc="handleChangeVal" attr_name1="radio2_value" attr_name2="radio2_img" attr_name3="radio2_text" attr_name4="radio2_img_src" padding_left="20px" question_text="Q2.  長時間の歩行・立ち仕事の後、最も悩む足のトラブルはどれですか？"/>
        </div>
        <a v-if="radio2_img_src" :href="radio2_img_src">
            <img class="radio_img" v-show="radio2_img" :src="radio2_img" alt="VIVAIA">
        </a>
        <img v-else class="radio_img" v-show="radio2_img" :src="radio2_img" alt="VIVAIA">

        <!-- question 3 -->
        <div class="content-radiu1" v-if="radio2_value" :style="{ background: `url(${data_1.bg_img}) no-repeat`}">
            <h2 class="title"><span>\</span> たった2問 <span>/</span></h2>
            <p class="desc">カンタン！30秒で完了！</p>
            <Progress :num="3"/>
            <AnserRadio :data="data_3" :radioValue="radio3_value" :imgsrc="radio3_img" @changefunc="handleChangeVal" attr_name1="radio3_value" attr_name2="radio3_img" attr_name3="radio3_text" attr_name4="radio3_img_src" padding_left="20px" question_text="Q3. その足のトラブルをどのように解決していますか？"/>
        </div>
        <a v-if="radio3_img_src" :href="radio3_img_src">
            <img class="radio_img" v-show="radio3_img" :src="radio3_img" alt="VIVAIA">
        </a>
        <img v-else class="radio_img" v-show="radio3_img" :src="radio3_img" alt="VIVAIA">

        <!-- question 4 -->
        <div class="content-radiu1" v-if="radio3_value" :style="{ background: `url(${data_1.bg_img}) no-repeat`}">
            <h2 class="title"><span>\</span> たった1問 <span>/</span></h2>
            <p class="desc">限定特典まであと一歩！</p>
            <Progress :num="4"/>
            <AnserCheckbox :data="data_4" :checkboxValue="radio4_value" :imgsrc="radio4_img" @changefunc="handleChangeVal" attr_name1="radio4_value" attr_name2="radio4_text_arr" padding_left="20px" :checkboxText="radio4_text_arr" question_text="Q4. Aria5°フラットシューズのどこに惹かれましたか？<br>【複数選択】" @handleSubmit="handleViewData"/>
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
        <a :href="radio4_img4_skip">
            <img class="radio_img" v-if="finished" :src="radio4_img4" alt="VIVAIA">
        </a>
    </div>
</template>

<script>
import AnserRadio from "./comp/radio"
import AnserCheckbox from "./comp/checkbox.vue"
import Progress from "./comp/progress.vue"
import { nanoid } from 'nanoid'

export default {
    components: {
        AnserRadio,
        AnserCheckbox,
        Progress
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
            radio4_img4: pt_hello_data.radio4_img4,
            radio4_img4_skip: pt_hello_data.radio4_img4_skip,
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
            font-size: 36px;
            line-height: 44px;
            margin-top: 60px;
            text-align: center;
            font-family: 'Noto Serif JP';
            font-weight: 900;
            color: #522F17;
        }
        .desc {
            font-size: 14px;
            line-height: 20px;
            text-align: center;
            font-family: 'Noto Serif JP';
            font-weight: 500;
            color: #2D2822;
        }
    }
    .radio_img {
        display: inline-block;
        width: 100%;
    }
    .radio_div_comp {
        width: 100%;
        height: 215px;
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
}
</style>