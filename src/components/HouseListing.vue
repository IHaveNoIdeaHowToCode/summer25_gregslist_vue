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
<div class="shadow rounded-top house-border">
  <img :src="houseProp.imgUrl" :alt="`A picture of ${houseProp.creator.name}'s house`" class="img-fluid">
  <div class="p-3 bg-light">
    <div>
      <p class="fs-3 fw-bold mb-0">
      {{ 'Year: ' + houseProp.year }}
      </p>
      <p class="fs-3 fw-bold mb-0">{{ 'Bedrooms: ' + houseProp.bedrooms }}
      </p> 
      <p class="fs-3 fw-bold mb-0">{{ 'Bathrooms: ' + houseProp.bathrooms }}
      </p> 
      <p class="fs-3 fw-bold mb-0">{{ 'Levels: ' + houseProp.levels }}
      </p> 
      <!-- <button @click="deleteHouse()"></button> -->
    </div>
    <p class="fs-5">
      {{ '$' + houseProp.price.toLocaleString() }}
    </p>
    <p>{{ houseProp.description }}</p> 
     <div class="d-flex justify-content-between align-items-center">
      <time :datetime="houseProp.createdAt.toLocaleDateString()">
      {{ houseProp.updatedAt.toLocaleDateString() }}
      </time>
    </div>
      <div>
        <span>{{ houseProp.creator.name }}</span>
        <img :src="houseProp.creator.picture" :alt="houseProp.creator.name" class="creator-img">
      </div>
  </div>
</div>


</template>


<style lang="scss" scoped>
.house-img {
  width: 100%;
  height: 40dvh;
  object-fit: cover;
}

.creator-img {
  height: 50px;
  aspect-ratio: 1/1;
  border-radius: 50%;
  object-fit: cover;
}

.house-border {
  border-style: double;
  border-width: thick;
  border-color: black;
  overflow-y: hidden;
}
</style>