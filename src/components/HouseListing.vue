<script setup>
import { AppState } from '@/AppState.js';
import { House } from '@/models/House.js';
import { houseService } from '@/services/HouseService.js';
import { logger } from '@/utils/Logger.js';
import { Pop } from '@/utils/Pop.js';
import { computed } from 'vue';



const props = defineProps({
  houseProp: {type: House, required: true}
})

const account = computed(() => AppState.account)

</script>


<template>
<div class="shadow rounded-top-house-border">
  <img :src="houseProp.imgUrl" :alt="`A picture of ${houseProp.creator.name}'s house`" class="img-fluid">
  <div class="p-3 bg-light">
    <div class="d-flex justify-content-between align-items-center mb-2">
      <p class="fs-3 fw-bold-mb-0">
        Year {{ houseProp.year }} {{ houseProp.bedrooms }} {{ houseProp.bathrooms }} {{ houseProp.levels }}
      </p>
      <!-- <button @click="deleteHouse()"></button> -->
    </div>
    
  </div>
</div>
</template>


<style lang="scss" scoped>

</style>