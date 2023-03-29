<template>
    <div class="progress-container">
        <div :class="`number ${num === 1 ? 'selected' : ''}`">01</div>
        <div class="split">
            <div class="split-circle"></div>
        </div>
        <div :class="`number ${num === 2 ? 'selected' : ''}`">02</div>
        <div class="split">
            <div class="split-circle"></div>
        </div>
        <div :class="`number ${num === 3 ? 'selected' : ''}`">03</div>
        <div class="split">
            <div class="split-circle"></div>
        </div>
        <div :class="`number ${num === 4 ? 'selected' : ''}`">04</div>
    </div>
</template>

<script>
export default {
    props: {
        num: {
            type: Number,
            default: 1,
            require: true
        }
    },
    data() {
        return {

        }
    }
}
</script>

<style lang="less" scoped>
.progress-container {
    height: 35px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: 28px;
    .number {
        width: 35px;
        height:35px;
        color: #8A552B;
        background: #ffffff;
        border-radius: 50%;
        font-size: 20px;
        line-height: 35px;
        text-align: center;
        font-family: "Noto Serif JP";
        font-weight: 700;
    }
    .selected {
        background: #79509A;
        color: #ffffff;
    }
    .split {
        height: 0px;
        width: 24px;
        border: 1px dashed #B8A17D;
        position: relative;
        margin: 0 7px;
        .split-circle {
            width: 6px;
            height: 6px;
            border-radius: 50%;
            background: #B8A17D;
            position: absolute;
            right: -1px;
            top: -3px;
        }
    }
}
</style>