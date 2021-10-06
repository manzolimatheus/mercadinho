<template>
  <div class="cart">
    <FaixaCarrinho :cart="cart" :total="total" :show_buttons="false" />
    <div class="container">
      <p v-if="cart.length < 1">Você ainda não inseriu nada no carrinho.</p>
      <div class="lista" v-for="item in cart" :key="item.id">
        <hr />
        <div class="wrapper">
          <div class="col-img">
            <img :src="item.img" :alt="item.nome" />
          </div>
          <div class="col-text">
            <h2>{{ item.nome }}</h2>
            <h5>R${{ item.preco }}</h5>
            <button class="button-remove" @click="RemoveItem(item)">
              Remover do carrinho
            </button>
          </div>
        </div>
      </div>
      <hr />
      <h1>Total: R${{ total.toFixed(2) }}</h1>
    </div>
  </div>
</template>

<script>
import FaixaCarrinho from "@/components/FaixaCarrinho.vue";

export default {
  name: "Cart",
  components: {
    FaixaCarrinho,
  },
  data() {
    return {
      cart: [],
      total: 0,
    };
  },
  methods: {
    Total() {
      this.cart.forEach((item) => {
        this.total += item.preco;
      });
    },
    RemoveItem(item) {
      const index = this.cart.indexOf(item);
      this.cart.splice(index, 1);
      this.total = 0;
      this.Total();
      localStorage.setItem("Cart", JSON.stringify(this.cart));
      this.Emit();
    },
    Emit() {
      this.$emit("update-preco", [this.total]);
    },
  },
  mounted() {
    if (localStorage.getItem("Cart") !== null) {
      this.cart = JSON.parse(localStorage.getItem("Cart"));
    }

    this.Total();
    this.Emit();
  },
};
</script>

<style scoped>
.container {
  padding: 5%;
}

.wrapper {
  display: grid;
  grid-template-columns: 20% 80%;
}

.col-img img {
  width: 50%;
}

.button-remove {
  color: tomato;
  background: none;
  border: 0;
}
</style>