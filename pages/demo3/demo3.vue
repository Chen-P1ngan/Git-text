<template>
	<view class="out">		
		<checkbox-group @change="itemChange">
			<view class="item" v-for="(item,index) in goods" :key="item.id">
				<checkbox :value="item.id" :checked="item.checked"></checkbox>
				<text class="title">{{item.name}}</text>
				<text class="price">{{item.price}}元</text>
				<text class="del" @click="remove(index)">删除</text>
			</view>
		</checkbox-group>
		
		<view class="card">
			<checkbox-group @change="allSelectChange">
				<label>
					<checkbox :checked="allSelectChecked"/><text>全选</text>
				</label>
			</checkbox-group>
			<view class="text">
				<view class="number">共{{totalNumber}}件商品</view>
				<view class="total">总计:{{totalPrice}}元</view>
			</view>			
		</view>
	</view>
</template>

<script setup>
import {computed, ref, watch} from "vue";
const goods = ref([
	{id:"11",name:"小米",price:4999,checked:false},
	{id:"22",name:"华为",price:8899,checked:false},
	{id:"33",name:"oppo",price:2688,checked:false},
	{id:"44",name:"苹果",price:9999,checked:false},
])

const allSelectChecked = ref(false);
const selectGroup = ref([]);
const totalPrice = computed(()=>goods.value.filter(item=>item.checked).reduce((prev,curr)=>prev+curr.price,0));
const totalNumber = computed(()=>selectGroup.value.length);

function itemChange(e){
	selectGroup.value = e.detail.value;
	goods.value = goods.value.map(item=>({
			...item,
			checked: selectGroup.value.includes(item.id)
	}));
}

function allSelectChange(e){
	allSelectChecked.value = !allSelectChecked.value;
	goods.value.forEach(item=>item.checked = allSelectChecked.value);
	selectGroup.value = allSelectChecked.value ? goods.value.map(item=>item.id):[];
}

function remove(index){
	goods.value.splice(index,1);
	selectGroup.value = goods.value.filter(item=>item.checked == true).map(item=>item.id);
}

watch(goods, () => {
	if(goods.value.length === 0)
		allSelectChecked.value = false;
	else
		allSelectChecked.value = goods.value.every(item=>item.checked);
},{deep:true});

</script>

<style lang="scss" scoped>
.out{
	padding:10px;
	.item{
		padding: 10px 0;
		.price{
			margin:0 20px;
		}
		.del{
			color:#c00;
			margin-left:30px;
		}
	}
	.card{
		border-top:1px solid #eee;
		margin-top:20px;
		padding:10px 0;
		display: flex;
		justify-content: space-between;
		align-items: center;
		.text{
			display: flex;
			align-items: center;
			.total{
				margin-left:20px;
			}
		}
	}
}
</style>
