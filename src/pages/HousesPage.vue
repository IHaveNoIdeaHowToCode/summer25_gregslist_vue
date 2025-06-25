<script setup>
import { AppState } from '@/AppState.js';
import HouseListing from '@/components/HouseListing.vue';
import { houseService } from '@/services/HouseService.js';
import { logger } from '@/utils/Logger.js';
import { Pop } from '@/utils/Pop.js';
import { computed, onMounted } from 'vue';


const house = computed(() => AppState.houses)

onMounted(() => {
  getHouses()
})

async function getHouses() {
  try {
    await houseService.getHouses()
  }
  catch (error){
    Pop.error(error);
    logger.error('FAILED TO GET HOUSES', error)
  }
}

</script>


<template>
  <section class="container">
    <div class="row">
      <div class="col-12">
        <div class="d-flex justify-content-center align-items-center">
          <h1 class="display-3">Houses <span class="mdi mdi-home"></span></h1>
          <!-- <button v-if="account" type="button" class="btn btn-outline-dark"></button> -->
           <small>Login so you can sell your home!</small>
        </div>
      </div>
    </div>
  </section>
  <section class="container">
    <div class="row">
      <HouseListing :houseProp="house" />
    </div>
  </section>
</template>


<style lang="scss" scoped>

</style>