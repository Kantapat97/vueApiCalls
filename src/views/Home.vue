<template>
  <!-- <div v-for="phone in Callblockings" v-bind:key="phone.id">
    <hr>
    <div>id: {{ phone.id }}</div>
    <div>phonenumber: {{ phone.phonenumber }}</div>
    <div>เจ้าของ: {{ phone.owner }}</div>
    <hr> -->
    <div class="container">
        <table class="table table-striped table-bordered">
            <thead>
                <tr>
                    <th>id</th>
                    <th>phonenumber</th>
                    <th>owner</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="phone in Callblockings" v-bind:key="phone.id">
                    <td>{{phone.id}}</td>
                    <td>{{phone.phonenumber}}</td>
                    <td>{{phone.owner}}</td>
                </tr>
            </tbody>
        </table>
    </div>    
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      Callblockings: [],
      errors: [],
    };
  },
  async created() {
    try {
      const response = await axios.get("http://localhost:4000/api/phone");
      this.Callblockings = response.data.data;
      console.log(response.data.data);
    } catch (e) {
      this.errors.push(e);
    }
  },
};
</script>
