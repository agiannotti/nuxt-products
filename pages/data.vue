<template>
  <div>
    <h1
      class="
        flex
        text-2xl text-red-800
        justify-center
        m-auto
        font-semibold
        pb-4
      "
    >
      Products
    </h1>
    <form class="">
      <label for="select"></label>
      <select
        class="flex p-1 justify-center m-auto border-2 w-2/3 text-gray-400"
        name="select"
        value="filter"
        label="{}"
      >
        <option disabled selected>Search Products...</option>
        <option>Show All</option>
        <option
          v-for="product in products"
          :key="product.id"
          :value="product.category"
        >
          {{ product.catname }}
        </option>
      </select>
    </form>
    <div class="container justify-center m-auto">
      <div class="flex flex-wrap justify-center">
        <Product
          v-for="product in products"
          :key="product.id"
          :product="product"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Product from '../components/Product'
export default {
  components: {
    Product,
  },
  data() {
    return { products: {} }
  },
  async getProducts() {
    // hit api with some axios
    const API_URL =
      'https://trayvonnorthern.com/Edgewood-API/public/api/products'
    const products = await this.$axios.$post(API_URL)
    // commit mutation
    console.log(products)
    return { products }
  },
}
</script>
