<template>
  <div class="city-bg">
    <span style="display: flex; justify-content: center; font-size: 20px; padding: 10px; font-weight: bold;">İl Detayları</span>
    <span style="font-weight: bold; margin-bottom: 6px;">İl Adı : <span style="font-weight: 500;">{{ cityDetailList.data[0].name }}</span></span>
    <span style="font-weight: bold; margin-bottom: 6px;">İl Plaka Kodu : <span style="font-weight: 500;">{{ cityDetailList.data[0].id }}</span></span>
    <span style="font-weight: bold; margin-bottom: 6px;">İl Nüfusu : <span style="font-weight: 500;">{{ cityDetailList.data[0].population.toLocaleString() }}</span></span>
    <span style="font-weight: bold; margin-bottom: 6px;">İl Metropol Mü : <span style="font-weight: 500;">{{ cityDetailList.data[0].isMetropolitan ? 'Evet' : 'Hayır' }}</span></span>
    <span style="font-weight: bold; margin-bottom: 6px;">Coğrafi Bölge : <span style="font-weight: 500;">{{ cityDetailList.data[0].region.tr }}</span></span>
    <span style="font-weight: bold; margin-bottom: 6px;">İl Koordinatları (Lat/Lon) : <span style="font-weight: 500;">{{ cityDetailList.data[0].coordinates.latitude }} / {{ cityDetailList.data[0].coordinates.longitude }}</span></span>
    <span style="font-weight: bold; margin-bottom: 6px;">İlçe Sayısı : <span style="font-weight: 500;">{{ cityDetailList.data[0].districts.length }}</span></span>
    <span style="font-weight: bold; margin-bottom: 6px;">İlçe Listesi : </span>
    <div v-for="districts in cityDetailList.data[0].districts" :key="districts.id">
        <span style="font-weight: bold; margin-bottom: 6px; margin-right: 20px;">İlçe Adı : <span style="font-weight: 500;">{{districts.name}}</span></span>
        <span style="font-weight: bold; margin-bottom: 6px;">İlçe Nüfusu : <span style="font-weight: 500;">{{ districts.population.toLocaleString() }}</span></span>

    </div>

</div>
</template>

<script>
export default {
    name:"CityDetail",
    props: {
        cityDetailList:{
            required: true
        }
    }

}
</script>

<style scoped>
.city-bg{
    border-radius: 7px;
    background: white;
    padding: 10px;
    display: flex;
    flex-direction: column;
}

</style>