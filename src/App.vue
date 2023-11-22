<template>
  <div class="background-style">
    <div style="display: flex; flex-direction: column; justify-content: center;">
      <h2 style="display: flex; justify-content: center; padding-top: 30px;">Türkiye İlleri Bilgi Sayfası</h2>
      <div style="display: flex;">
        <input type="text" placeholder="İl giriniz" v-model="searchCity"
          style="width: 50%; padding: 20px; display: flex; justify-content: center; margin-top: 20px; margin-left: 380px;">
        <button @click="searchButton"
          style="width: 60px; height: 50px; border-radius:7px; background-color: chocolate; border-color: chocolate; color: white; margin-top: 25px; margin-left: 10px;">Ara</button>
      </div>
      <span style="display: flex; justify-content: center; margin-top: 20px; font-weight: bold;" v-if="isError">Lütfen geçerli bir il yazın</span>
    </div>
    <div style="margin: 20px 500px;" v-if="isVisible">
      <city-detail :cityDetailList="cityDetailList"></city-detail>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
import axios from 'axios';
import CityDetail from './components/CityDetail.vue';
export default {
  name: 'App',
  components: { CityDetail },
  setup() {
    const searchCity = ref('');
    const isVisible = ref(false);
    const isError = ref(false);
    const cityDetailList = ref([]);
    const searchButton = () => {
      if (searchCity.value !== '') {
        axios.get("https://turkiyeapi.cyclic.app/api/v1/provinces?name=" + searchCity.value).then((payload) => {
          cityDetailList.value = payload.data;
          isVisible.value = true;
          searchCity.value = "";
          isError.value = false;
        }).catch((err) => {
          if(err){
            isError.value = true;
          }
        });
      }

    }

    return { searchCity, searchButton, isVisible, cityDetailList,isError }
  }

}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.background-style {
  width: 100%;
  height: 100vh;
  background-image: url('https://c4.wallpaperflare.com/wallpaper/885/999/821/istanbul-4k-night-turkey-wallpaper-preview.jpg');
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
