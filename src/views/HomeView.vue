<template>
  <img src="https://www.freeiconspng.com/uploads/quran-icon-png-7.png" style="width: 300px; margin-bottom: 20px">
    <div class="surah">
      <!-- eslint-disable-next-line -->
      <li class = "card" style="width: 18rem;" v-for="item in daftarsurah">
        {{item.name_simple +" ("+item.name_arabic + ") "}}
        <p>{{item.translated_name.name}}</p>
        <p>{{item.verses_count + ' ayat '}}</p>
        <p>{{'Surah ' + item.revelation_place}}</p>
        <router-link :to="{name: 'surah', params: {id: item.id}}" class="btn btn-primary" style="background-color: cadetblue">baca</router-link>
      </li>
    </div>
</template>

<script>
import {ref} from "vue";
import axios from "axios";

export default {
  data() {
    return{
      daftarsurah : ref([])
    }
  },
  mounted(){
    this.getDaftarSurah()
  },
  methods:{
    getDaftarSurah(){
      axios.get('https://api.quran.com/api/v4/chapters?language=id')
          .then ((respons) =>
          {
            console.log(respons)
            this.daftarsurah = respons.data.chapters
          })
          .catch((err) =>
          {
            console.log('error' + err)
          })
    }
  }
}
</script>

<style>
li{
  list-style: -moz-ethiopic-numeric;
}
.surah{
  display: flex;
  flex-wrap: wrap;
  alignment: center;
  padding-left: 20px;
}
p{
  color: black;
}
.card{
  text-align: center;
  margin-left: 50px;
  margin-bottom: 20px;
  padding-top: 20px;
}

.btn-primary{
  alignment: center;
  margin-left: 20%;
  width: 10rem;
  background-color: cadetblue;
  margin-bottom: 10px;
}
template{
  padding-bottom: 20px;
}
</style>
