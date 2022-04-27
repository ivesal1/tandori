<template>
  <div class="mt-8">
      <div>
          <div class="flex justify-end">
              منو
          </div>
          <div class="flex justify-end mt-2">
              <underLine/>
          </div>
      </div>
    <div class="grid-baba mt-8">
        <div class="" v-for="mbutton in mbuttons" :key="mbutton.data">
            <nuxtLink :to="mbutton.code">
            <div class="flex flex-row justify-center cursor-pointer items-center buttons-style mx-1">
                <div class="buttons-name-color">{{mbutton.name}}</div>
                <div><img class="icon-width" :src=mbutton.icon></div>
            </div>
            </nuxtLink>
        </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    data(){
        return {
            mbuttons:[]
        }
    },
    created(){
        this.mfetchSomething().then(res => {
            this.mbuttons = res.data.data
            console.log(this.mbuttons);
        });
    },
    methods : {
        mfetchSomething () {
            try {
                return axios.get('https://tandori.ir/plus/v1/categories'); 
            } catch (error) {
                console.error(error);
                console.log(this.mbuttons);
            }
        },
    }
}
</script>

<style scoped>
    .grid-baba {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        grid-template-rows: repeat(3, 1fr);
        grid-column-gap: 50px;
        grid-row-gap: 34px;
        }
.icon-width{
    width: 40px;
    height: 40px;
}
</style>