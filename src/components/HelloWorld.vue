<template>
  <div class="hello">
    {{ post }}
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      post: null,
    };
  },
  async mounted() {
    this.post = await axios.get("http://localhost:5000/getListRandom").then((res) => {
      console.log(res.data.msg)
      return res.data.msg;}).catch((err) => console.log(err))
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
  }
}
;

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
