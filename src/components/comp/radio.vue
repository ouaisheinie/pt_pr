<template>
    <div class="answer-container">
        <div class="answer-radio">
            <img class="prod-img" v-if="data.img" :src="data.img" alt="VIVAIA" />
            <div class="radio-style radio-not-finally" :style="{ paddingLeft: padding_left}" v-for="(item, index) in data.radio_list" :key="index" @click="handleSelect" :data-val="item.value" :data-text="item.text" :data-imgsrc="item.radio_img" :data-imgskip="item.img_src">
                <input class="radio" type="radio" :name="item.radio_name" :value="item.value">
                <div class="radio-virtual">
                    <img v-if="Number(radioValue) === index + 1" src="../../assets/radio_icon1.png" alt="VIVAIA">
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
        radioValue: {
            type: Number,
            default: undefined
        },
        attr_name1: {
            type: String
        },
        attr_name2: {
            type: String
        },
        attr_name3: {
            type: String
        },
        attr_name4: {
            type: String
        },
        padding_left: {
            type: String
        }
    },
    methods: {
        handleSelect(e) {
            this.$emit('changefunc', this.attr_name1, Number(e.target.dataset.val))
            this.$emit("changefunc", this.attr_name2, e.target.dataset.imgsrc)
            this.$emit("changefunc", this.attr_name3, e.target.dataset.text)
            this.$emit("changefunc", this.attr_name4, e.target.dataset.imgskip)
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
            width: 15px;
            height: 15px;
            border-radius: 50%;
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

