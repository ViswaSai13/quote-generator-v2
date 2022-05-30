<template>
  <div id="quotesDiv" class="flex-grow text-white-smoke-xd text-center ph8 pt6 overflow-y-a">
    <div class="border-all border-width-3 br8 w100p pv4 ph3 mb6" v-for="(quote, index) in quoteArr" :key="index">
        <div class="pv3 f26">
          {{ quote.text }}
        </div>
        <div class="pv3 f22 italic">
          - {{ quote.author }}
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Quotes',
  props:{
    quoteArr: Array
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
#quotesDiv{
  height: 100vh
}
</style>