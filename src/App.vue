<template>
  <div class="app">
    <HeaderComponent title="Random Quotes with Vue.js" />
    <QuoteComponent :quote="quote" />
    <div class="button-container">
      <button @click="getQuote">NEW QUOTE</button>
    </div>
  </div>
</template>

<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import QuoteComponent from "./components/QuoteComponent.vue";

export default {
  name: "App",
  components: {
    HeaderComponent,
    QuoteComponent
  },
  data() {
    return {
      quote: {
        text: "",
        author: ""

      },
      quotes: []
    };
  },
  created() {
    this.getQuote();
  },
  methods: {
    async getQuote() {
      const data = await fetch("https://type.fit/api/quotes").then(res => res.json());
      const randomQuote = Math.floor(Math.random() * data.length);
      if (this.quote.content) {
        this.quotes = [...this.quotes, this.quote];
      }

      this.quote = {
        text: data[randomQuote].text,
        author: data[randomQuote].author
      };
    }
  }
};
</script>

<style lang="scss">
:root {
  --primary: #42b883;
  --secondary: #35495e;
  --dark: #1a1a1a;
  --lite: #e1e1e1;
  --gray: #2f2f2f;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.button-container {
  display: flex;
  justify-content: center;
  padding: 0 20px;
  margin: 40px auto;
  button {
    color: var(--primary);
    border: none;
    background-color: var(--secondary);
    padding: 10px 20px;
    font-size: 22px;
    border-radius: 20px;
    cursor: pointer;
    transition: 0.4s;

    &:hover {
      background-color: var(--gray);
    }
  }
}
</style>

