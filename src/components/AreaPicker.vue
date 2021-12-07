<template>
  <div class="w-[120px] h-[40px] rounded bg-white relative z-1  border-r border-l" @click="setState('isCity')">
    <span class="leading-[40px] text-[#696969] text-sm">
      {{currCity+currArea}}
      <i-mdi-arrow-up-drop-circle class="w-[16px] h-[16px] ml-1 mt-2" />
    </span>
    <template>

    </template>
      <div class="w-[350px] bg-[#fff] border-b border-r border-l border-[#F0F0F0] flex flex-wrap justify-start py-4 absolute left-0 top-[39.5px]">
        <div class="w-[85px] h-[32px] text-sm space-x-1" v-for="(city,idx) in cities" :key="city" >  
          <div class="w-[13px] h-[13px] inline-block border-[1px] rounded "></div>
          <label class="text-[#696969]" :for='idx' @click="setState('isArea')">
            {{city}}
            <input type="radio" v-model="currCity" class="hidden" :id="idx" :value="city">
          </label> 
        </div> 
      </div> 
      
      <div class="w-[350px] bg-[#fff] border-b border-r border-l border-[#F0F0F0] flex flex-wrap justify-start py-4 absolute left-0 top-[39.5px]">
        <div class="w-[85px] h-[32px] text-sm space-x-1" v-for="(city,idx) in areaList" :key="city">  
          <div class="w-[13px] h-[13px] inline-block border-[1px] rounded "></div>
          <label class="text-[#696969]" :for='idx'>
            {{city}}
            <input type="radio" v-model="currArea" class="hidden" :id="idx" :value="city">
          </label> 
        </div> 
      </div> 
  </div>
</template>

<script>
import areaData from '@/assets/area.json';
import { reactive, toRefs, computed } from 'vue'
export default {
  setup(){
    const state = reactive({
      currState:'',
      setState: (status) => state.currState = status
    });
    const cities = [];
    const areaList = computed(() => (currSelectItem.currCity)? areaData[currSelectItem.currCity] :[]);

    for(const key in areaData){ 
      cities.push(key);
    };
    const currSelectItem = reactive({
      currCity:'台北市',
      currArea:'全區',
    })

    return{
      cities,
      areaList,
      ...toRefs(currSelectItem),
      ...toRefs(state),
      
    }
  }
}
</script>

<style>

</style>