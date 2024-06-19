<template>
	<view class="template-index">
		 <tn-nav-bar :isBack="false">{{tabbarList[currentIndex].title}}</tn-nav-bar>
		<view class="template-body tn-flex tn-flex-direction-column" :style="{paddingTop: vuex_custom_bar_height + 'px'}" >
			<swiper :indicator-dots="false" :current="currentIndex" style="height: 100%;width:100%; " @change="change">
				<swiper-item>
					<view class="pages-item"> 
						<pageA ></pageA> 
					</view>
				</swiper-item>
				<swiper-item>
					<view class="pages-item">
						 <pageB></pageB>
					</view>
				</swiper-item>
				<swiper-item>
					<view class="pages-item">
					 <pageC></pageC>
					</view>
				</swiper-item>
			</swiper>
		</view>
		<view>
			<tn-tabbar  v-model="currentIndex" :list="tabbarList" @change="change"></tn-tabbar>
		</view>
	</view>
</template>

<script>
	import pageA from './components/pageA.vue'
	import pageB from './components/pageB.vue'
	import pageC from './components/pageC.vue'
	export default {
		components: {
			pageA,
			pageB,
			pageC
		},
		data() {
			return {
				currentIndex: 0,
				tabbarList: [{
						title: '首页',
						activeIcon: 'home-fill',
						inactiveIcon: 'home'
					},
					{
						title: '发现',
						activeIcon: 'honor',
						inactiveIcon: 'honor',
						activeIconColor: '#FFFFFF',
						inactiveIconColor: '#FFFFFF',
						iconSize: 50,
						out: true
					},
					{
						title: '我的',
						activeIcon: 'my-fill',
						inactiveIcon: 'my'
					}
				],
			}
		},
		onLoad() {
				
		},
		methods: {
			// 计算tabbar高度 
			change(value) {
				if(value?.detail){
					this.currentIndex=value.detail.current
				}else{
					this.currentIndex=value;
				} 
			}
		}
	}
</script>

<style lang="scss" scoped>
	.template-index {
		height: 100vh;
		width: 100vw;
		display: flex;
		overflow: hidden;
		flex-direction: column;
		background-color: $tn-bg-color; 
	}
	.template-body{ 
		flex: 1; 
	}
	.pages-item{
		height: 100%; 
		overflow: hidden; 
	}
</style>