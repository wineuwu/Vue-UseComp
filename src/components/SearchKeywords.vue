<template>
  <div class="inline-block text-lg">
    <div class="custom-search relative h-[40px]">
      <input 
      type="text" 
      v-model.trim="keyword"
      class="px-2 w-[320px] p-1 focus:outline-none h-[40px] border-b rounded 
      "
      >
      <i-uil-search class="text-xl text-[#eee] absolute right-[10px] top-0 bottom-0 my-auto text-[#BEBEBE]" />
    </div>
  </div>
</template>

<script>
import { reactive, toRefs, watch, computed } from 'vue'
export default {
  setup(){
    const searchVal = reactive({
      keyword:''
    });

    //autocomplete
    let timer;  
    watch(
      () =>searchVal.keyword,
      (newVal) => {
        clearTimeout(timer);
        timer = setTimeout(() => {
          if(newVal){
            console.log('is stop typing current is keywords --> ',newVal);
          }
        },1000)
      }
    );

    return {
      ...toRefs(searchVal)
    }
  }
}
</script>

<style>

</style>