<template>
  <div>
      <button class="p-2 bg-black">salam</button>
      <div v-for="button in buttons" :key="button.data">
          <div>{{button.code}}</div>
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

<style>

</style>