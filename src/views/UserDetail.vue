<template>
  <div>
    <h3>{{ userDetail.name }}</h3>

    <h2>{{ userDetail.usernmae }}</h2>

    <p> {{ userDetail.address }} </p>
  </div>
</template>

<script>

import axios from "axios";


export default {
  name: "UserDetail",
  data() {
    return {
      userDetail: "",
      userId: ""
    };
  },
  methods: {
    async getUser() {
        axios({
        method: "get",
        url: `https://jsonplaceholder.typicode.com/users/${this.userId}`,
      })
        .then((res) => {
          console.log(res.data);
          this.userDetail = res.data;
        })
        .catch((err) => {
          console.warn(err);
        });
    },
  },
  mounted() {
    this.userDetail = this.$route.params.item;
    this.userId  = this.userDetail.id
    this.getUser()
  },
};
</script>
