<template>
	<view class="navbar">
		<view class="navbar-fix">
			<!-- 状态栏 -->
			<view :style="{height: statusBarHeight + 'px'}"></view>
			<!-- 导航栏内容 -->
			<view class="navbar-content" :style="{width: windowWidth + 'px', height: navbarHeight + 'px'}">
				<view class="nav-bar_search" :style="{height: searchHeight + 'px'}">
					<view class="navbarsearch_icon">
						<uni-icons type="search" size="16" color="#999"></uni-icons>
					</view>
					<view class="navbarsearch_text">uni-app text</view>
				</view>
			</view>
		</view>
		<view :style="{height: (navbarHeight + statusBarHeight) + 'px'}">

		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				statusBarHeight: 20,
				navbarHeight: 45,
				windowWidth: 375,
				searchHeight: 32,
			};
		},
		created() {
			// 获取手机信息
			const info = uni.getSystemInfoSync()
			// 设置状态栏高度
			this.statusBarHeight = info.statusBarHeight
			this.windowWidth = info.windowWidth
			// #ifndef H5 || APP-PLUS || MP-ALIPAY
			// 获取胶囊的位置
			const menuButtonInfo = uni.getMenuButtonBoundingClientRect()
			
			// (胶囊底部高度 - 状态栏高度) + (胶囊顶部高度 - 状态栏高度) = 导航栏
			this.navbarHeight = (menuButtonInfo.bottom - info.statusBarHeight) +(menuButtonInfo.top - info.statusBarHeight)
			this.windowWidth = menuButtonInfo.left
			this.searchHeight = menuButtonInfo.height
			// #endif
		}
	}
</script>

<style lang="scss">
	@import '../../common/css/icons.css';
	.navbar {
		.navbar-fix {
			position: fixed;
			top: 0;
			left: 0;
			z-index: 99;
			width: 100%;
			background-color: $mk-base-color;

			.navbar-content {
				display: flex;
				align-items: center;
				justify-content: center;
				padding: 0 15px;
				box-sizing: border-box;

				.nav-bar_search {
					display: flex;
					width: 100%;
					height: 30px;
					border-radius: 30px;
					padding: 0 10px;
					background-color: #fff;
					align-items: center;

					.navbarsearch_icon {
						margin-right: 10px;
					}

					.navbarsearch_text {
						font-size: 12px;
						color: #999999;
					}
				}
			}

		}
	}
</style>
