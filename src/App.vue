<template>
	<div>
        <div v-if="visible">
            <Header />
            <Content :data="data_1" :changeloading="changeLoading" />
            <div class="loading" v-if="loading">
                <div class="loading-animate"></div>
            </div>
        </div>
        <div v-else style="text-align: center;">
            there is no options in this page
        </div>
	</div>
</template>

<script>
import "./index.css"
import Header from "./components/headComp.vue"
import Content from "./components/content.vue"

export default {
	name: 'App',
	components: {
		Header,
		Content
	},
    data() {
        return {
            visible: false,
            loading: false
        }
    },
    mounted() {
        if (window.pt_hello_data) {
            this.visible = true
        }
    },
    methods: {
        changeLoading(val) {
            this.loading = val
        }
    }
}
</script>

<style lang="less">
* {
	margin: 0;
	padding: 0;
}
.loading {
    width: 100vw;
    height: 100vh;
    position: fixed;
    top: 0;
    left: 0;
    background: rgba(0, 0, 0, .3);
    display: flex;
    justify-content: center;
    align-items: center;
    .loading-animate {
        display: inline-block;
        width: 30px;
        height: 30px;
        vertical-align: middle;
        animation: loading-bar-spinner 400ms linear infinite;
        border: solid 4px transparent;
        border-top-color: white !important;
        border-left-color: white !important;
        border-radius: 50%;
    }
    @keyframes loading-bar-spinner {
        0% {
            transform: rotate(0deg);
            transform: rotate(0deg);
        }
        100% {
            transform: rotate(360deg);
            transform: rotate(360deg);
        }
    }
}
</style>
