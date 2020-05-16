<template>
  <div>
    <h1>ハローワールドですね</h1>
    <p>Body: {{ body }}</p>
    <p>Datetime: {{ datetime }}</p>
    <button @click="getHello">更新するよ</button>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'hello',
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
