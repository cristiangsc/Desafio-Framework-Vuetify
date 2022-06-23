<template>
  <div class="text-xs-center" v-if="products.length">
    <v-item-group>
      <v-container>
        <v-row>

          <Product-item
              v-for="product in paginatedData"
              :product="product"
              :key="product.id"
              @addToCart="addProductToCart"
          >
          </Product-item>
        </v-row>

      </v-container>
    </v-item-group>
    <v-pagination v-show="products.length" v-model="page" :length="pages"></v-pagination>
  </div>
  <v-alert v-else
           dense
           outlined
           type="error"
  >
    No existen <strong>Productos</strong> que mostrar en este momento
  </v-alert>

</template>

<script>
import {mapState, mapActions} from 'vuex';
import ProductItem from "@/components/ProductItem";

export default {
  components: {
    ProductItem
  },
  mounted() {
    this.fetchProducts();
  },
  data() {
    return {
      rowsPerPage: 5,
      page: 1
    }
  },
  computed: {
    ...mapState('products', ['products']),

    pages() {
      return this.rowsPerPage ? Math.ceil(this.products.length / this.rowsPerPage) : 0
    },
    paginatedData() {
      return this.products.slice((this.page * this.rowsPerPage) - this.rowsPerPage, (this.page * this.rowsPerPage));
    }
  },
  methods: {
    ...mapActions('products', ['fetchProducts']),
    addProductToCart(product) {

    }
  }
}

</script>


<style scoped>

</style>