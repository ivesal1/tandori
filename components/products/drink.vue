<template>
    <div class=" mt-8 ">
        <div >
            <div class="flex justify-end page-title">دوره های نوشیدنی</div>
            <div class="flex justify-end mt-2"><underLine/></div>
        </div>

        <div class="md:flex md:justify-center overflow-auto overflow-x-scroll ml-20">
            <div class="salam-chetori px-3 mt-8" v-for="drink in drinks" :key="drink.data">
                <div :style="{ 'background-image':`url('${drink.pictures.cover}')` }" class="course-pic bgimg-adjust">
                    <div>
                    <h1 class=" pt-3 pl-3">دوره تاندوری</h1>
                    </div>
                    <div class="">
                        <div class="course-chef bgimg-adjust" :style="{ 'background-image':`url('${drink.pictures.main}')`}"></div>
                    </div>
                </div>
                <div class="mt-4">
                        <div style="font-size:15px;font-weight:600;" class="text-right mt-3">دوره {{drink.name}}</div>
                        <div style="font-weight:400; font-size:14px ;color: rgb(193, 193, 193);" class="text-right mt-4">{{drink.slang}}</div>
                        <div class="mt-6" style="color: rgb(255, 255, 255); font-weight: 600;">{{drink.price.original}} <span style="font-size:12px;">تومان</span></div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data(){
        return {
            drinks :[]
        }
    },
     created(){
        this.fetchDrink().then(res => {
            this.drinks = res.data.data.items
            console.log(this.drinks);
        });
    },
    methods : {
        fetchDrink () {
            try {
                return axios.get('https://tandori.ir/plus/v1/categories/details?code=drink'); 
            } catch (error) {
                console.error(error);
                console.log(this.drikns);
            }
            // axios.get('https://tandori.ir/plus/v1/categories/details?code=sweets').then(res=>{
            //     this.seewts = res.data.data
            //     console.log(res);
            // })
        },
    }
}

</script>

<style>

</style>