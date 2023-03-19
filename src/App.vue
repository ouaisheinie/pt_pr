<template>
	<div>
		<Header />
		<Content :data="data_1" @changeData="handleChangeData"/>
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

        }
    },
    mounted() {

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
