<template>
  <div>
    <div class="suara">
      <p></p>
      <audio :src="audio.audio_url" controls>
        </audio>
    </div>
      <li v-for="(ayatQuran,index) in ayat">
          <p> {{ayatQuran.text_uthmani  }} {{ ayatQuran.verse_key }} </p>
          <p v-html="Arti[index].text"></p>
      </li>
  </div>
  <section>
    
  </section>
</template>
<script>
import {ref} from "vue";
import axios from "axios";



export default {
  data() {
      return {
          ayat: ref([]),
          Arti: ref([]),
          audio: ref([])
      }
  },
  mounted() {
      this.getAyat()
      this.getArti()
      this.getAudio()
  },
  methods: {
      getAyat() {
      axios.get(`https://api.quran.com/api/v4/quran/verses/uthmani?chapter_number=${this.$route.params.id}`)
          .then((response) => {
            console.log(response)
            this.ayat = response.data.verses
          })
          .catch((err) => {
            console.log('error' + err)
          })
    },
    getArti() {
      axios.get(`https://api.quran.com/api/v4/quran/translations/33?chapter_number=${this.$route.params.id}`)
          .then((respons) => {
            console.log(respons)
            this.Arti = respons.data.translations
          })
          .catch((err) => {
            console.log('error' + err)
          })
    },
    getAudio() {
      axios
          .get(`https://api.quran.com/api/v4/chapter_recitations/7?chapter=${this.$route.params.id}`)
          .then((response) => {
            this.audio = response.data.audio_files[0];
          })
          .catch((error) => {
            console.log(error);
          });
    }
  }
}
</script>
<style scoped>
 li{
  list-style: none;
   text-align: center;
 }
</style>