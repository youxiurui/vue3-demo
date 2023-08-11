<template>
    <h1>商品和库存管理</h1>
    <input type="text" v-model="data.shopName" style="width:200px;margin-right:5px;">
    <input type="number" v-model="data.shopCount" style="width:50px;margin-right:5px;">
    <button @click="addShop">添加</button>
    <ul>
        <li v-for="(shop,index) in data.shopLis" :key="index">
            <span>{{ shop.name }}</span>
            <button style="margin:0 5px;" @click="shop.count>0?shop.count--:shop.count=0">-</button>
            <span style="color:rgb(0, 174, 255);width:35px;display:inline-block;">{{ shop.count>0?shop.count:'售完' }}</span>
            <button style="margin:0 5px;"  @click="shop.count++">+</button>
            <input type="number" v-model="shop.count" min="0" style="width:50px;margin-right:5px;">
            <button @click="delShop(index)">删除</button>
        </li>
    </ul>
</template>

<script setup>
import {reactive} from "vue"

const data=reactive({
    shopName:'',
    shopCount:0,
    shopLis:[
        {
            name:'小米',
            count:0
        }
    ]
})

function addShop(){
    const shop={
        name:data.shopName,
        count:data.shopCount
    }
    data.shopName=''
    data.shopCount=0
    data.shopLis.push(shop)
}

function delShop(index){
    data.shopLis.splice(index,1)
}

</script>

<style scoped>

</style>
