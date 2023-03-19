<template>
    <div class="answer-radio">
        <img class="prod-img" :src="data.img" alt="VIVAIA" />
        <div class="radio-style radio-not-finally" v-for="(item, index) in data.radio_list1" @click="handleSelect" :data-val="item.value">
            <input class="radio" type="radio" :name="item.radio_name" :value="item.value">
            <div class="radio-virtual">
                <img v-if="Number(radioValue) === index + 1" src="../../assets/radio_icon1.png" alt="VIVAIA">
            </div>
            はい
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
        }
    },
    methods: {
        handleSelect(e) {
            this.$emit('changefunc', 'radio1_value', Number(e.target.dataset.val))
        }
    }
}
</script>

<style lang="less" scoped>
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
        padding-left: 42px;
        box-sizing: border-box;
        border-radius: 5px;
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
            img {
                display: inline-block;
                width: 100%;
                height: 100%;
            }
            margin-right: 5px;
        }
    }
    .radio-not-finally {
        margin-bottom: 10px;
    }
}
</style>

