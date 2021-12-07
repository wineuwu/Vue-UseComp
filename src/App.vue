<template>
  <div class="w-full h-full ">
    <div class="search-bar m-auto border-b border-[#eee] max-w-[640px]  bg-[#eee]
     text-center flex items-center h-[80px] justify-center space-x-2">
      <AreaPicker />
      <SearchKeywords />
    </div>
    
  </div>
</template>

<script>

import { reactive, toRefs } from 'vue';


export default {
  setup() {

  },
}
</script>

<style>

</style>