<template>
  <li v-for="(item,index) in daftarsurah">
    <router-link :to="{name: 'surahdetail', params: {id: item.id}}">
      <div class="surah flex p-3" data-id="{{ item.id }}" tabindex="0">
          <div class="flex">
            <div class="surah__eg-name flow">
              <p>{{ item.name_complex }}</p>
            </div>
          </div>
          <div class="surah__ar-name flow">
            <p>{{ item.translated_name.name }}</p>
            <p>
              <span>{{ item.verses_count }}</span> Ayat
            </p>
            <button type="button" class="btn btn-outline-info">Baca Surah</button>
          </div>
        </div>
    </router-link>
    <hr>
  </li>
</template>

<script>
import {ref} from "vue";
import axios from "axios";
export default {
    data() {
      return {
        daftarsurah: ref([])
      }
    },
    mounted() {
      this.getDaftarSurah()
    },
    methods: {
      getDaftarSurah() {
        axios.get("https://api.quran.com/api/v4/chapters?language=id")
            .then((respons) =>
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

<style scoped>
li {
list-style: none;
text-align: center;
}


</style>