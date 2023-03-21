<template>
	<div>
        <div v-if="visible">
            <Header />
            <Content :data="data_1" @changeData="handleChangeData"/>
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
        }
    },
    mounted() {
        if (window.pt_hello_data) {
            this.visible = true
        }
    },
    methods: {
        handleChangeData(name, data) {
            this[name] = data
        }
    }
}
</script>

<style>
* {
	margin: 0;
	padding: 0;
}
</style>
