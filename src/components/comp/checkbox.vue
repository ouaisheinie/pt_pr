<template>
    <div class="answer-container">
        <div class="answer-radio">
            <img class="prod-img" v-if="data.img" :src="data.img" alt="VIVAIA" />
            <div class="radio-style radio-not-finally" :style="{ paddingLeft: padding_left}" v-for="(item, index) in data.radio_list" :key="index" @click="handleSelect" :data-val="item.value" :data-imgsrc="item.radio_img" :data-text="item.text">
                <input class="radio" type="checkbox" :name="item.radio_name" :value="item.value">
                <div class="radio-virtual">
                    <img v-if="checkboxValue.includes(index + 1)" src="../../assets/checkbox.png" alt="VIVAIA">
                </div>
                {{ item.text }}
            </div>
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
            this.$emit('changefunc', this.attr_name1, arr)
            this.$emit("changefunc", this.attr_name2, arr_text)
        }
    }
}
</script>

<style lang="less" scoped>
.answer-container {
    padding: 0 20px;
}
.answer-radio {
    padding: 35px 33px 30px;
    background: #ffffff;
    border-radius: 10px;
    margin-top: 10px;
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
        background: #F3EADB;
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
            width: 20px;
            height: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            background: #ffffff;
            margin-right: 10px;
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

