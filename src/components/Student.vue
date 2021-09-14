<template>
  <div>
  <h1 style="color:black;">Student Data</h1>
  <div style="overflow-x:auto;">
  <table style="width:100%" class="table">
      <tr>
        <th>Name</th>
        <th>Email</th>
        <th>Phone</th>
        <th>Website</th>
        <th>Company</th>
      </tr>
      <tr v-for="item in list" v-bind:key="item.id">
        <td>{{item.name}}</td>
        <td>{{item.email}}</td>
        <td>{{item.phone}}</td>
        <td>{{item.website}}</td>
        <td>{{item.company.name}}</td>
      </tr>
    </table>
    </div>
  </div>
</template>

<script >
import Vue from "vue";
import axios from "axios";
import VueAxios from "vue-axios";
Vue.use(VueAxios, axios);
export default {
  name: "student",
  data() {
    return {
      list: undefined,
    };
  },
  mounted() {
    Vue.axios
      .get("https://jsonplaceholder.typicode.com/users")
      .then((response) => {
        this.list = response.data;
        console.warn(response.data);
      });
  },
};
</script>
<style >
.table {
  color: black;
  border: 1px solid black;
}
table, th, td {
  border:1px solid black;
}
h1{
  margin-top:50px;
}

</style>
