<template>
	<view class="out">
		<input type="text" :value="iptValue" @focus="isActive=false" @blur="isActive=true"/>
		<image src="/static/chicken.gif" class="pic" :class="isActive?'active':''"></image>
	</view>
</template>

<script setup>
import { ref } from 'vue';
const iptValue = ref("")
const isActive = ref(false)

// function onfocus(e){
// 	isActive.value = false;
// }

// function onblur(e){
// 	isActive.value = true;
// }
// 
</script>

<style lang="scss" scoped>
.out{
	padding: 0 20px;
	margin-top: 40px;
	position: relative;
	input{
		border: 1px solid #ccc;
		height: 40px;
		position: relative;
		z-index: 2;
		background-color: #fff;
	}
	.pic{
		width: 24px;
		height: 24px;
		z-index: 1;
		position: absolute;
		top: -24px;
		left: calc(50% - 12px);
		transition: top 0.3s;
	}
	.pic.active{
		top: 0;
	}
}
</style>
