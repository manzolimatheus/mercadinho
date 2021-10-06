<template>
  <div class="container-carrinho">
    <Cart @update-preco="SavePreco" />
    <div class="buttons">
      <router-link to="/items"
        >Continuar comprando <ion-icon name="cart-outline"></ion-icon
      ></router-link>
      <a @click="Finalize"
        >Finalizar compra <ion-icon name="arrow-forward-outline"></ion-icon
      ></a>
    </div>
  </div>
</template>

<script>
import Cart from "@/components/Cart.vue";

export default {
  name: "Carrinho",
  components: {
    Cart,
  },
  data() {
    return {
      preco: 0,
    };
  },
  methods: {
    SavePreco(preco) {
      this.preco = preco;
    },
    Finalize() {
      this.$router.push({
        name: "Final",
        params: {
          preco: this.preco,
        },
      });
    },
  },
};
</script>

<style scoped>
.buttons a {
  background-color: #36bd5e;
  padding: 2%;
  color: white;
}
</style>