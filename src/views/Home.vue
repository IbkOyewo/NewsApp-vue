<template>
<div>  
  <div>
      <Main />
  </div>
  <div class="latest-news">
    <h3>Latest News</h3>
  </div>

  
  
  <div class="card-container">
     <div class="card" v-for="allNews in getAllNews" :key="allNews.id">
       <a class="all-links" :href="allNews.url" target="_blank">
            <img v-if="allNews.urlToImage" :src="allNews.urlToImage" class="img" alt="img"/>
            <img v-else :src="imgUrl" class="img" alt="img" />
            <p class="title info">{{allNews.title}}</p>
            <p class="read-more" :href="allNews.url" target="_blank">Read more...</p>
            <p class="info date">Data Published: {{allNews.publishedAt}}</p>
        </a>
        </div>
    </div>

</div>
</template>

<script>
import { mapActions, mapGetters } from 'vuex'
import Main from '@/components/Main.vue'
export default {
  name: "Home",
  components: {
    Main
  },
  data() {
    return {
      imgUrl: 'https://www.9news.com.au/assets/img/9news-image-background.96245abf.jpg'
    }
  },

  computed: {
    ...mapGetters(['getAllNews'])
  },
  mounted() {
    this.fetchAllNews()
  },
  methods: {
    ...mapActions(['fetchAllNews'])
  }

}
</script>

<style scoped>
 .latest-news {
   padding: 30px;
 }
 a{
    color: black;
    text-decoration: none;
}
 h3 {
   margin-top: 20px;
   font-size: 40px;
   font-weight: 500;
 }
 .card-container {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-between;
  margin-bottom: 20px;
  padding: 40px;
  margin-left: 80px;
  margin-right: 80px;
}
.card {
  margin-top: 40px;
  border-radius: 10px;
  box-shadow: rgba(0, 0, 0, 0.1) 0px 20px 25px -5px, rgba(0, 0, 0, 0.04) 0px 10px 10px -5px;
  display: flex;
  flex-direction: column;
  width: 360px;
  margin-bottom: 20px;
}
.img {
  width: 100%;
  height: 15rem;
  object-fit: cover;
  cursor: pointer;
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
}
.info {
  text-align: left;
  margin-left: 20px;
  margin-right: 20px;
  cursor: pointer;
  margin-top: 40px;
  margin-bottom: 20px;
}
.card:hover {
  background-color: ghostwhite;
}
.title {
  font-weight: 500;
  font-size: 24px;
}
.title:hover {
  color: rgb(90, 9, 138);
}
.date {
  font-size: 10px;
  font-style: italic;
  color: rgb(90, 9, 138);
}
</style>
