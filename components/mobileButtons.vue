<template>
  <div>

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