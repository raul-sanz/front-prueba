<template>
  <div class="mt-12 px-6 flex justify-center">
   
      
    <div class="grid">
       <vs-row >
      <vs-col  v-for="(article , index) in data"  :key="article.url"   lg="4" xs="12" sm="6" >
        <Card  :article="article" :index="index"/>
      </vs-col>
    </vs-row>
    </div>
  </div>
</template>

<script>
import Card from '@/components/Card';
import axios from "axios";
export default {
  components:{'Card':Card},
  data(){
    return{
      data :[]
    }
  },
  mounted( ) {
    return axios
      .get(
        `https://newsapi.org/v2/everything?q=apple&from=2020-09-15&pageSize=11&to=2020-10-15&sortBy=popularity&apiKey=d6736e08a3ac4859aeda69469b97d4cc`
      )
      .then((res) => {
        console.log(res.data)
         this.data= res.data.articles
      });
  },
};
</script>

<style>


</style>

