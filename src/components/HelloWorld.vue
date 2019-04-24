<template>
  <div>
    <div> {{ title }} </div>
    <SearchForm @val1="searchGiphys"/>
    <div>
      <ul>
        <li v-for="gift in images">                    
            <a v-bind:href="gift.url"><img v-bind:src="gift.url"/></a>
        </li>
      </ul>
    </div>
   </div>
</template>

<script>
import Axios from 'axios';
import SearchForm from "./SearchForm.vue";
export default {
  name: 'Practica',  
  data () {
    return {
      title: "Practica",
      images: []
    }
  },
  components: {
    SearchForm
  },
  methods: {
    searchGiphys(newSearch) {
       Axios.get("http://api.giphy.com/v1/gifs/search?q="+newSearch+"&api_key=R2y0EOkKV21cQd2oos1TZHBIUsgDaVmh&limit=5")
        .then((response) => {
          const resp = response.data.data;
          for (const gift in resp) {
            this.images.push({url: resp[gift].images.preview_gif.url});            
          }
        })
        .catch((err) => {
          console.log(err);
        });
    }
  },
  created () {
   
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
