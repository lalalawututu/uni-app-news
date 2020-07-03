<template>
	<view class="scroll">
		<scroll-view class="list-scroll" scroll-y="true">
			<view>
				<view class="" v-for="item in 100">
					{{item}}neir
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			};
		}
	}
</script>

<style lang="scss">
	.scroll {
		flex: 1;
		box-sizing: border-box;
		overflow: hidden;
		border: 5px solid red;

		.list-scroll {
			height: 100%;
			display: flex;
			flex-direction: column;
		}
	}
</style>
