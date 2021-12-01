<template>
    <div v-if="!loading">
        <data-title :text="title" :dataDate="dataDate" />

        <data-boxes :stats="stats"/>

        <country-select @get-country="getCountryData" :countries="countries" />
    </div>

    <main v-else class="loader">
        <div>
            <img :src="loadingImage" alt="">
        </div>
    </main>
</template>

<script>
import DataTitle from '../components/DataTitle.vue'
import CountrySelect from '../components/CountrySelect.vue'
import DataBoxes from '../components/DataBoxes.vue'


export default {

  name: 'Home',
  components: {
    DataTitle, DataBoxes , CountrySelect
  },
  data(){
    return{
      loading:true,
      countries:[],
      title:'Global',
      dataDate:'',
      stats:{},
      loadingImage:require('../assets/loading.gif')
    }
  },
  methods:{
    async fetchCovidDate(){
      const res = await fetch('https://api.covid19api.com/summary')
      const data =await res.json()
      return data
    },
    getCountryData(country){
      this.stats = country;
      this.title = country.Country
    }
  },
  async created(){
    const data = await this.fetchCovidDate();
    this.dataDate = data.Date;
    this.stats = data.Global
    this.countries = data.Countries
    this.loading = false
  }
}
</script>


<style scoped>
    .loader{
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }

    .loader img{
      width: 100px;
    }
</style>