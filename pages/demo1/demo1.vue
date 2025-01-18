<template>
	<view>
		这是demo1
	</view>
	
	<view>
		{{2 + 3}}
		{{a}}
	</view>
	<view>{{Date.now()}}</view>
	<view>{{Math.random()}}</view>
	<view>{{1<2 ? "张三":"李四"}}</view>
	<view>{{ fn() }}</view>
</template>

<script setup>
	const a = 6;
	
	function fn(){
		return "vue3学习"
	}
</script>

<style>
	       
</style>
