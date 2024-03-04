<template>
  <div>
    Выберете денежную валюту:
    <select size="1" v-model="currency">
      <option>₽</option>
      <option>€</option>
      <option>$</option>
    </select>
    <div v-for="product in products" :key="product.id" class="products_cars">
      <p>Название: {{ product.name }}</p>
      <p>Цена: {{ formattedPrice(product.price) }}</p>
      <p v-if="product.available">Статус: Available</p>
      <p v-else>Статус: Out of stock</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductDetails",

  data() {
    return {
      name: "",
      currency: "",
      products: [
        {
          id: 1,
          name: "Geely",
          price: 2500000,
          available: true,
        },
        {
          id: 2,
          name: "Exceed",
          price: 3800000,
          available: false,
        },
        {
          id: 3,
          name: "Tank",
          price: 2000000,
          available: true,
        },
      ],
    };
  },

  computed: {
    formattedPrice() {
      if (this.currency === "₽") {
        return (price) => `${price} рублей`;
      } else if (this.currency === "€") {
        return (price) => `€ ${(price / 100.3).toFixed(2)}`;
      } else {
        return (price) => `$ ${(price / 94.71).toFixed(2)}`;
      }
    },
  },

  mounted() {},

  methods: {},
};
</script>

<style>
.products_cars {
  border: 1px solid black;
  padding: 20px;
  width: 200px;
  margin-top: 20px;
}
</style>
