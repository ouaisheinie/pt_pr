<template>
    <div class="header">
        <a href="#question-1">
            <img class="header-img" :src="img1" alt="VIVAIA">
        </a>
        <a href="https://lp.vivaia.jp/Bestshoes-for-longtime-walkingandstanding">
            <img class="content-img" :src="img2" alt="VIVAIA">
        </a>
    </div>
</template>

<script>
export default {
    data() {
        return {
            img1: pt_hello_data.header_img1,
            img2: pt_hello_data.header_img2
        }
    }
}
</script>

<style lang="less" scoped>
.header {
    font-size: 0px;
    .header-img, .content-img {
        display: inline-block;
        width: 100%;
    }
}
</style>