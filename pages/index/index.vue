<template>
	<view class="box" hover-class="boxHover">
		<view class="inner" hover-class="innerHover" hover-stop-propagation>内部元素</view>
	</view>
	
	<view>-----------------</view>
	
	<text selectable="true">文本标签</text>
	
	<view>
		<navigator url="/pages/demo1/demo1">跳转到demo1</navigator>
	</view>
	
	<view>
		<navigator url="/pages/demo2/demo2">跳转到demo2</navigator>
	</view>
	
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>


	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
	
	.box {
		width: 200px;
		height: 200px;
		background: #ccc;
	}
	
	.boxHover {
		background: orange;
		width: 300px;
	}
	
	.inner {
		width: 150px;
		height: 150px;
		background: green;
	}
	
	.innerHover {
		background: greenyellow;
	}
	
	
	
	
</style>
