<template>
  <div>
      <mobileButtons/>
  </div>
</template>

<script>
import mobileButtons from '~/components/mobileButtons'
export default {
    components:{
        mobileButtons
    }
}
</script>

<style>
icon-width{
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