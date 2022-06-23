<template>
  <v-card
      class="mx-auto mb-4"
      max-width="400"
  >
    <v-img
        class="white--text align-end"
        height="200px"
        :src="product.picture"
    >
      <v-card-title></v-card-title>
    </v-img>

    <v-card-subtitle class="pb-0">
      Descripción: {{ product.name }}
    </v-card-subtitle>

    <v-card-text class="text--primary">
      <div>Valor $ {{ product.price }}</div>
    </v-card-text>

    <v-card-actions>
      <v-btn
          color="orange"
          text
          @click="$emit('addToCart', product)"
      >
        Añadir al carrito
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  name: "ProductItem",
  props: {
    product: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>

</style>