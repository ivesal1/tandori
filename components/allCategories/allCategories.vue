<template>
<div class="md:flex md:flex-row-reverse mt-8 ml-30">
    <div  class="salam-chetori md:mx-3 mt-8 md:ml-0 adjust-product" v-for="product in products" :key="product.data">
        <div style="">
            <div :style="{ 'background-image':`url('${product.pictures.cover}')` }" class="course-pic bgimg-adjust">
               <div>
                   <h1 class="font-size-tandori-top pt-3 pl-3">دوره تاندوری</h1>
               </div>
               <div class="">
                    <div class="course-chef bgimg-adjust" :style="{ 'background-image':`url('${product.pictures.main}')`}"></div>
                </div>
            </div>
        </div>
        <div class="mt-4">
            <div style="font-size:15px;font-weight:600;" class="text-right mt-3">دوره {{product.name}}</div>
            <div style="font-weight:400; font-size:14px ;color: rgb(193, 193, 193);" class="text-right mt-4">آشپزی با {{product.slang}}</div>
            <div class="mt-6" style="color: rgb(255, 255, 255); font-weight: 600;">{{product.price.priceBeforeTax}} <span style="font-size:12px;">تومان</span></div>
        </div>
    </div>
</div>
</template>

<script>
import axios from 'axios'
export default {
    data (){
        return {
            products : [],
            certificate:'دارای گواهی گذراندن دوره'
        }
    },created(){
        this.fetchSomethings().then(res => {
            this.products = res.data.data.data.items
            console.log(this.products);
        });
    }
    ,
    methods : {
        fetchSomethings(){
            try {
                return axios.get('https://tandori.ir/plus/v1/courses/list?limit=5&page=1')
            } catch(error) {
                console.error(error);
                // console.log(this.products);
            }
        },
    }
}
</script>

<style>
    .bgimg-adjust{
       background-size: cover;
    background-repeat: no-repeat;
    background-position: 50%;
}
.course-pic {
    width: 100%;
    height: 0;
    padding-bottom: 140%;
    border-radius: 20px;
    position: relative;
}
.wrapper{
    display: flex!important;
    flex-direction: row;
}
.position-relative {
    position: relative!important;
}
.course-chef{
    width: 50px;
    height: 50px;
    border-radius: 100%;
    position: absolute;
    bottom: 12px;
    right: 12px;
    border: 1px solid #252525;
}
.font-size-tandori-top{
    font-size: 15px;
    font-weight: 900;
}

.wrapper ,.items {
    flex-shrink: 5;
}

@media (min-width: 300px) and (max-width: 640px){
    .adjust-product{
        margin-left:100px;
    }
}
</style>