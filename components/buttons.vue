<template>
  <div class="mt-8">
    <div class="flex flex-row justify-end">
        <div v-for="button in buttons" :key="button.data">
            <div class="flex flex-row items-center buttons-style mx-1">
                <div class="buttons-name-color">{{button.name}}</div>
                <div><img class="icon-width" :src=button.icon></div>
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
            buttons:[]
        }
    },
    // async asyncData() {
    //     const buttons = await axios.get('https://tandori.ir/plus/v1/categories')
    //     return {
    //         buttons : buttons
    //     }
    // },
    created(){
        this.fetchSomething().then(res => {
            this.buttons = res.data.data
            console.log(this.buttons);
        });
    },
    methods : {
        fetchSomething () {
            try {
                return axios.get('https://tandori.ir/plus/v1/categories'); 
            } catch (error) {
                console.error(error);
                console.log(this.buttons);
            }
        },
    }
}
</script>

<style scoped>
    .icon-width{
        width:26px;
        height: 26px;
    }
    .buttons-style{
        border-radius: 20px;
        padding:3px 10px;
        background-color: #23272e;

    }
    .buttons-name-color{
        color:#eaeaea
    }
</style>