<template>
  <h1>بِسْمِ اللَّهِ الرَّحْمَنِ الرَّحِيم </h1>
  <div class="mb-5">
    <div v-for="(ayat, index) in ayatquran" :key="index" class="card">
      <div class="card-body text-center">
        <h5 class="card-title Ayat d-inline display-5 align-center">{{ayat.text_uthmani}}</h5>
        <br />
        <div class="mt-3">
          <p class="card-text mt-3 d-inline"><strong> {{ayat.verse_key}} Artinya : </strong></p>
          <p class="card-text mt-3 artiAyat d-inline" v-html="artiayat[index].text"></p>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
import axios from 'axios'
import {ref} from 'vue'

export default {
  data() {
    return {
      ayatquran: ref([]),
      artiayat: ref([])
    }
  },
  mounted(){
    this.getAyatQuran(),
    this.getArtiAyat()
  },
  methods: {
    getAyatQuran(){
      axios.get(`https://api.quran.com/api/v4/quran/verses/uthmani?chapter_number=${this.$route.params.id}`)
          .then ((respons ) => {
            console.log(respons)
            this.ayatquran = respons.data.verses
          }).catch((err) => {
        console.log('error' + err)
      })
    },
    getArtiAyat(){
      axios.get(`https://api.quran.com/api/v4/quran/translations/33?chapter_number=${this.$route.params.id}`)
          .then ((respons ) => {
            console.log(respons)
            this.artiayat = respons.data.translations
          }).catch((err) => {
        console.log('error' + err)
      })
    },
  }
}
</script>

<style scoped>
li {
  list-style: none;
  margin-top: 8%;
}
.mb-5{
  margin-right: 20px;
  padding-bottom: 50px;
  margin-bottom: 0px;
}
template{
  margin-bottom: 0;
  padding-bottom: 30px;
}
h1{
  color: white;
  padding-bottom: 15px;
}
</style>