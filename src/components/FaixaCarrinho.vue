<template>
  <div class="carrinho">
    <h2>Itens no carrinho: {{ cart.length }}</h2>
    <h2>R$Total: {{ total.toFixed(2) }}</h2>
    <div class="buttons" v-show="show_buttons">
      <button @click="EsvaziarCarrinho">
        Esvaziar carrinho<ion-icon name="trash-bin-outline"></ion-icon>
      </button>
      <router-link to="/cart">
        Ir para o carrinho
        <ion-icon name="arrow-forward-outline"></ion-icon>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "FaixaCarrinho",
  props: {
    cart: Array,
    total: Number,
    show_buttons: Boolean,
  },
  methods: {
    EsvaziarCarrinho() {
      localStorage.removeItem("Cart");
      this.$emit("empty-cart");
    },
  },
};
</script>

<style>
.carrinho {
  background-color: #36bd5e;
  padding: 1%;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  text-align: center;
}

.carrinho h2 {
  padding-inline: 2%;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}

.buttons a,
button {
  background-color: white;
  padding: 1%;
  border-radius: 10px;
  color: black;
  border: 0;
  font-size: 12pt;
  text-align: center;
  margin: 1%;
}

@media (max-width: 768px){
  .carrinho{
    grid-template-columns: 100%;
  }

  .buttons a, button{
    font-size: large;
    padding: 3%;
  }
}
</style>