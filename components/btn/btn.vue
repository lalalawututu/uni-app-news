<template>
	<view class="btns" :style="{color: color}" @click="onClick">
		<slot></slot>
	</view>
</template>

<script>
	export default {
		props: {
			color: {
				type: String,
				default: '#000',
			}
		},
		data() {
			return {
				
			};
		},
		methods: {
			onClick() {
				console.log('beijianji');
				this.$emit('change', this.color);
			}
		}
	}
</script>

<style>
	.btns{
		width: 100px;
		height: 100px;
		border: 1px red solid;
	}
</style>
