<template>
    <div class="answer-container">
        <div class="question" v-html="question_text"></div>
        <div class="answer-radio">
            <img class="prod-img" v-if="data.img" :src="data.img" alt="VIVAIA" />
            <div class="radio-style radio-not-finally" :style="{ paddingLeft: padding_left}" v-for="(item, index) in data.radio_list" :key="index" @click="handleSelect" :data-val="item.value" :data-imgsrc="item.radio_img" :data-text="item.text">
                <input class="radio" type="checkbox" :name="item.radio_name" :value="item.value">
                <div class="radio-virtual" :data-val="item.value" :data-imgsrc="item.radio_img" :data-text="item.text">
                    <img v-if="checkboxValue.includes(index + 1)" src="../../assets/radio_icon1.png" alt="VIVAIA" :data-val="item.value" :data-imgsrc="item.radio_img" :data-text="item.text">
                </div>
                {{ item.text }}
            </div>
        </div>
        <div class="submit" v-if="checkboxValue.length">
            <button class="submit-btn" @click="handleViewData">回答完了</button>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        data: {
            type: Object,
            default: {}
        },
        checkboxValue: {
            type: Array,
            default: []
        },
        checkboxText: {
            type: Array,
            default: []
        },
        attr_name1: {
            type: String
        },
        attr_name2: {
            type: String
        },
        padding_left: {
            type: String
        },
        question_text: {
            type: String,
            default: ""
        }
    },
    methods: {
        handleSelect(e) {
            const val = Number(e.target.dataset.val)
            const textVal = e.target.dataset.text
            let arr = JSON.parse(JSON.stringify(this.checkboxValue))
            let arr_text = JSON.parse(JSON.stringify(this.checkboxText))
            if (arr.includes(val)) {
                arr.forEach((item, index) => {
                    if (item === val) {
                        arr.splice(index, 1)
                    }
                })
                arr_text.forEach((item, index) => {
                    if (item === textVal) {
                        arr_text.splice(index, 1)
                    }
                })
            } else {
                arr.push(val)
                arr_text.push(textVal)
            }
            console.log(arr)
            this.$emit('changefunc', this.attr_name1, arr)
            this.$emit("changefunc", this.attr_name2, arr_text)
        },
        handleViewData() {
            this.$emit('handleSubmit')
        }
    }
}
</script>

<style lang="less" scoped>
.answer-container {
    padding: 0 20px;
    .question {
        font-size: 20px;
        line-height: 30px;
        font-family: "Noto Serif JP";
        font-weight: 700;
        background: #ffffff;
        border-top-left-radius: 5px;
        border-top-right-radius: 5px;
        padding: 24px 16px 10px;
        color: #8A552B;
        text-align: center;
    }
    .submit {
        text-align: center;
        .submit-btn {
            font-size: 16px;
            height: 40px;
            line-height: 20px;
            padding: 10px 80px;
            color: #ffffff;
            border: none;
            display: inline-block;
            margin: 0 auto;
            border-radius: 5px;
            margin-top: 10px;
            font-family: "Noto Serif JP";
            background: #FFB1C9;
        }
    }
}
.answer-radio {
    padding: 0px 33px 30px;
    background: #ffffff;
    border-radius: 10px;
    border-radius: 5px;
    .prod-img {
        display: inline-block;
        width: 100%;
        margin-bottom: 20px;
    }
    .radio-style {
        width: 100%;
        height: 40px;
        line-height: 40px;
        border: 1px solid #C3B2A4;
        color: #8A552B;
        font-size: 12px;
        display: flex;
        align-items: center;
        box-sizing: border-box;
        border-radius: 5px;
        font-family: "Noto Serif JP";
        font-weight: 500;
        .radio {
            position: absolute;
            left: -999999px;
        }
        .radio-virtual {
            width: 15px;
            height: 15px;
            border-radius: 50%;
            display: flex;
            border: 1px solid #8A552B;
            justify-content: center;
            align-items: center;
            background: #ffffff;
            margin-right: 16px;
            img {
                display: inline-block;
                width: 100%;
                height: 100%;
            }
        }
    }
    .radio-not-finally {
        margin-bottom: 10px;
    }
}
</style>

