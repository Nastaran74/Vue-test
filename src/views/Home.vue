<template>
  <div class="home">
    <div v-if="isLoading">
      <h4>Is Loading</h4>
    </div>
    <div v-else v-for="item in data" :key="item.name">
      <card-list :data="item" class="m-4" @click="showDetail(item)"></card-list>
      <button @click="showDetail(item)">Detail</button>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

import CardList from "../components/Card-list.vue";
import axios from "axios";

export default {
  name: "Home",
  components: {
    CardList,
  },
  data() {
    return {
      data: null,
      isLoading: true,
      activeItem: "home",
    };
  },
  methods: {
    async getData() {
      this.isLoading = true;
      axios({
        method: "get",
        url: "https://jsonplaceholder.typicode.com/users",
      })
        .then((res) => {
          this.isLoading = false;
          console.log(res.data);
          this.data = res.data;
        })
        .catch((err) => {
          console.warn(err);
          this.isLoading = false;
        });
    },

    showDetail(item) {
      this.$router.push({
        name: "detail", //use name for router push
        params: { item },
      });
    },
  },
  mounted() {
    this.getData();
  },
};
</script>
