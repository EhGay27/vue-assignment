<template>
  <div class="header">
    <h3 class="nrc">FOOD LIST</h3>
  </div>

  <button @click="addproduct" class="add">Add Product</button>

  <div class="card">
    <table class="table table-bordered">
      <thead class="table-dark">
        <tr>
          <th>Name</th>
          <th>Item_Name</th>
          <th>Description</th>
          <th>Price</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody v-if="this.foodlist.length > 0">
        <tr v-for="(foodlist, index) in this.foodlist" :key="index">
          <td>{{ foodlist.name }}</td>
          <td>{{ foodlist.itemname }}</td>
          <td>{{ foodlist.description }}</td>
          <td>{{ foodlist.price }}</td>
          <td>
            <button type="button" class="btn btn-success">Edit</button>

            <button type="button" class="btn btn-danger">
              Delete
            </button>
          </td>
        </tr>
      </tbody>
      <tbody v-else>
        <tr>
          <td colspan="5">Loading...</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>


<script>
import axios from 'axios'

export default {
  name: 'foodlist',
  data() {
    return {
      foodlist: []
    }
  },

  mounted() {
    this.getFoodlist();
  },



  methods: {
    getFoodlist() {
      axios.get('http://localhost:8000/api/foodlist').then(res => {
        this.foodlist = res.data.Foodlist
      });
    }
  },
}
</script>



