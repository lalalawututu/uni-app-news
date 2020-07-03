<template>
	<view class="tab">
		<scroll-view scroll-x="true" class="tab-scroll">
			<view class="tab-scroll_box">
				<view class="tab-scroll_item" :class="{active: activeIndex === index}" :key="index" v-for="(item, index) in list" @click="clickTab(item,index)">
					{{item.name}}
				</view>
			</view>
		</scroll-view>
		<view class="tab-icons">
			<uni-icons type="gear" size="26" color="#666"></uni-icons>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			list:{
				type: Array,
				default() {
					return []
				}
			}
		},
		data() {
			return {
				activeIndex: 0,
			};
		},
		methods:{
			clickTab(item,index){
				this.activeIndex = index
				this.$emit('tab',{
					data:item,
					index:index
				})
			}
		}
	}
</script>

<style lang="scss">
	.tab {
		display: flex;
		width: 100%;
		box-sizing: border-box;
		background: #FFFFFF;
		border-bottom: 1px solid #f5f5f5;

		.tab-scroll {
			flex: 1;
			overflow: hidden;
			box-sizing: border-box;
			.tab-scroll_box {
				display: flex;
				height: 45px;
				align-items: center;
				flex-wrap: nowrap;
				box-sizing: border-box;

				.tab-scroll_item {
					flex-shrink: 0;
					padding: 0 10px;
					color: #333;
					font-size: 14px;
					&.active{
						color: $mk-base-color;
					}
				}
			}
		}

		.tab-icons {
			position: relative;
			width: 45px;
			display: flex;
			align-items: center;
			justify-content: center;
			&::after{
				content: '';
				position: absolute;
				top: 12px;
				bottom: 12px;
				left: 0;
				width: 1px;
				background-color: #ddd;
			}
		}
	}
</style>
