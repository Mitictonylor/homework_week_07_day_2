<template lang="html">
  <div>
    <div id="filterInput">
      <h3>Filter tweets</h3>
      <input type="number" v-model.number="filterTweets" min="0">
    </div>

      <div v-for="(tweet,index) in filteredTweets" :key="index">
      <TweetsItem v-bind:tweet="tweet"></TweetsItem>
      </div>

  </div>
</template>

<script>

import TweetsItem from './TweetsItem.vue';

export default {
  name: "Tweets",

  props:["tweets"],

  data() {
    return{
        filterTweets: 0
          }
        },

  computed:{
    filteredTweets: function(){
      return this.tweets.filter((tweet) => { return tweet.likes >= this.filterTweets})
    }
  },

  components: {
    TweetsItem
  }
}

</script>

<style lang="css" scoped>
</style>
