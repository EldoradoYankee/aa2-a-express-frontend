<template>
  <div class="hello">
    <h1>Zufälliges Zitat {{ row }}</h1>
    <h3>{{ sentence }}</h3>
    <h2>{{ author }}</h2>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      sentence: "",
      author: "",
      row : null,
    };
  },
  async mounted() {
    await axios
      .get("https://unr8c7h3d5.execute-api.eu-central-1.amazonaws.com/staging/getRandom")
      .then((res) => {
        console.log(res.data);
        this.sentence = res.data.Sentences;
        this.author = res.data.Author;
        this.row = res.data.row;
      })
      .catch((err) => console.log(err));
  },
  methods: {
    /**
    getListRandom: function() {
      console.log("me the button was clicked!")
      axios
          .get("localhost:5000/getListRandom").then((res) => {
            this.post = res.data;
          })
      console.log(this.post);
    }*/
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
 justify-content: center;
  align-content: center;
  height: 100vh;
  width: 100vw;
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
