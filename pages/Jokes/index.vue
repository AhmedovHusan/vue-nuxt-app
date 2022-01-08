<template>
  <div>
    <SearchJoke @search-text="searchText" />
    <div v-for="joke in jokes" :key="joke.id">
      <Joke :joke="joke.joke" :id="joke.id" />
    </div>
  </div>
</template>

<script>
import Joke from "../../components/Joke.vue";
import SearchJoke from "../../components/SearchJoke.vue";
import axios from "axios";
export default {
  components: {
    Joke,
    SearchJoke,
  },
  data() {
    return {
      jokes: [],
    };
  },
  async created() {
    const config = {
      headers: {
        Accept: "application/json",
      },
    };

    try {
      const res = await axios.get("https://icanhazdadjoke.com/search", config);
      this.jokes = res.data.results;
    } catch (err) {
      console.log(err);
    }
  },
  head() {
    return {
      title: "Dad Jokes",
      meta: [
        {
          hid: "description",
          name: "description",
          contenst: "Best place to read bad dad jokes here",
        },
      ],
    };
  },
  methods: {
    async searchText(text) {
      const config = {
        headers: {
          Accept: "application/json",
        },
      };

      try {
        const res = await axios.get(
          `https://icanhazdadjoke.com/search?term=${text}`,
          config
        );
        this.jokes = res.data.results;
      } catch (err) {
        console.log(err);
      }
    },
  },
};
</script>

<style></style>
