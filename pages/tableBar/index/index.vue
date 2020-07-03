<template>
	<view class="home">
		<navbar></navbar>
		<tab :list="tabList" @tab="tab"></tab>
		<list-scroll></list-scroll>
	</view>
</template>

<script>
	import navbar from '@/components/navbar/navbar.vue';
	// import tab from '@/components/tab/tab.vue';
	export default {
		components: {
			navbar
		},
		data() {
			return {
				title: "hel",
				className: "active",
				tabList: []
			}
		},
		onLoad() {
			this.getLabel()
		},
		methods: {
			tab({
				data,
				index
			}) {
				console.log(data, index);
			},
			getLabel() {
				this.$api.get_label({
					name: 'get_label'
				}).then((res) => {
					const {
						data
					} = res
					this.tabList = data
				})
			}
		}
	}
</script>

<style lang="scss">
	page{
		height: 100%;
		display: flex;
	}
	.home{
		display: flex;
		flex-direction: column;
		flex: 1;
	}
</style>