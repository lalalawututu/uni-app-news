<template>
	<view>		
		<view v-bind:class="className">
			{{title}}
		</view>
		<btn color="red" @change="change">点击</btn>
		<view class="style">
			样式
		</view>
	</view>
</template>

<script>
	import btn from '@/components/btn/btn.vue'
	export default {
		components: {
			btn: btn
		},
		data() {
			return {
				title: "hel",
				className: "active"
			}
		},
		onLoad() {
			uni.getSystemInfo({
				success(res) {
					console.log('成功：',res)
				},
				fail(err) {
					console.log('失败：',err)
				},
				complete(res) {
					console.log('完成：',res)
				}
			})
		},
		methods: {
			change(e) {
				console.log('输出 '+ e)
			}
		}
	}
</script>

<style lang="scss">
	.style{
		width: 100px;
		height: 100px;
		color: #007AFF;
		background: red;
	}
</style>
