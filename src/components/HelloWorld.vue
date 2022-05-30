<template>
  <div id="helloWorld" class="flex flex-row">
    <Filters />
    <Quotes :quoteArr="quoteArr"/>
  </div>
</template>

<script>
import Filters from './filters.vue'
import Quotes from './quotes.vue'

export default {
  name: 'HelloWorld',
  components: {
    Filters,
    Quotes
  },
  data(){
    return{
      quoteArr: [],
      apiUrl: 'https://type.fit/api/quotes',
      apiQuotes: [],
      authorArr: {}
    }
  },
  created(){
    this.getQuotes();
  },
  methods: {
    async getQuotes () {
      console.log('func called');
      try {
        const response = await fetch(this.apiUrl);
        this.apiQuotes = await response.json();
        this.quoteArr = this.apiQuotes
        this.getAuthors();
      } catch (error) {
        // this.getAuthors();
        console.log('API Error', error)
      }
    },
    getAuthors(){
      this.apiQuotes.forEach(element => {
        if(this.authorArr[element.author]){
          this.authorArr[element.author]++
        } else {
          this.authorArr[element.author] = 1
        }
      });
      console.log(this.authorArr, 'getAuthors Fn')
    }
  },
}
</script>

<style scoped lang="scss">
#helloWorld {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  // text-align: center;
  // color: #2c3e50;
  // margin-top: 60px;
  background-image: url("https://source.unsplash.com/Hlkuojv_P6I/1920x1280");
  background-repeat: no-repeat;
  background-size: cover;
  min-height: 100vh;
}
</style>
