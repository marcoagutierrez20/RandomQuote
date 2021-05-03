<template>
  <div class="quote" id="quote-box"> <!-- User Story #1 id="quote-box"-->
      <section class="card">
        <h4 id="authour">{{quotes[0][quoteNum].author}}</h4> <!-- User Story #3 id="author"-->
        <p id="text">{{quotes[0][quoteNum].text}}</p> <!-- User Story #2 id="text" -->
        <a href="https://twitter.com/intent/tweet" target="_blank" class="fa fa-twitter header-icon-one" id="tweet-quote"></a> <!-- User Story #5 id="tweet-quote" -->
        <button id="new-quote" @click="getQuote">New Quote </button> <!-- user Story #4 id="new-quote"-->
      </section>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Quote',
  data() { 
    return {
      quotes: [],
      quoteNum: 0
    }
  },

  mounted () {
    this.getQuotes();
  },

  methods: {
    getQuotes() {
      axios.get("https://type.fit/api/quotes")
      .then((res) => {
        this.quotes.push(res.data);
      }) 
      .catch((err) => {
        console.log(err)
      })
    },

    getQuote() {
      
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
