<template>
  <div class="hello">
    <h1>ハローワールドですね</h1>
    <p>Body: {{ body }}</p>
    <p>Datetime: {{ datetime }}</p>
    <button @click="getHello">更新するよ</button>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Hello',
  data() {
    return {
      body: '',
      datetime: null,
    };
  },
  methods: {
    async getHello() {
      const response = await axios.get('/api');
      this.body = response.data.body;
      this.datetime = response.data.datetime;
    },
  },
  created() {
    axios.defaults.baseURL = process.env.VUE_APP_API_BASE_URL;
  },
  mounted() {
    this.getHello();
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
