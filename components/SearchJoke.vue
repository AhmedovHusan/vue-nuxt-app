<template>
  <div>
    <form @submit="onSubmit">
      <input type="text" v-model="text" placeholder="Search Jokes..." />
      <input type="submit" value="Submit" />
    </form>
  </div>
</template>

<script>
export default {
  name: "SearchJoke",
  data() {
    return {
      text: "",
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      this.$emit("search-text", this.text);
      this.text = "";
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  padding: 20px;
  background: #f4f4f4;
  border: 1px solid #ddd;
  border-radius: 10px;
}
input[type="text"] {
  flex: 2;
  padding: 5px 10px;
  border: none;
  outline: none;
  background: transparent;
  font-size: 19px;
}
input[type="submit"] {
  padding: 5px 10px;
  border: none;
  color: #444;
  cursor: pointer;
  letter-spacing: 1.5px;
  font-size: 17px;
}
</style>
