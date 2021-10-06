<template>
  <div class="items">
    <FaixaCarrinho
      :cart="precart"
      :total="total"
      :show_buttons="true"
      @empty-cart="ClearItems"
    />
    <div class="data-loading">
      <h1>Items</h1>
      <hr />
      <div class="data">
        <div v-for="array in items" :key="items.indexOf(array)">
          <div v-for="item in array" :key="item.id">
            <Card :nome="item.nome" :img="item.img" :preco="item.preco" />
            <button class="adicionar" @click="UpdateCart(item)">
              <h3>
                <ion-icon name="add-circle-outline"></ion-icon> Adicionar ao
                carrinho
              </h3>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Card from "@/components/Card.vue";
import Cart from "@/components/Cart.vue";
import FaixaCarrinho from "@/components/FaixaCarrinho.vue";

export default {
  name: "Data",
  components: {
    Card,
    Cart,
    FaixaCarrinho,
  },
  props: {
    url: String,
  },
  data() {
    return {
      items: [],
      precart: [],
      total: 0,
    };
  },
  methods: {
    async LoadAcougue() {
      fetch("http://localhost:3000/acougue")
        .then((response) => response.json())
        .then((item) => {
          this.items.push(item);
        });
    },
    async LoadPadaria() {
      fetch("http://localhost:3000/padaria")
        .then((response) => response.json())
        .then((item) => {
          this.items.push(item);
        });
    },
    async LoadHortifruti() {
      fetch("http://localhost:3000/hortifruti")
        .then((response) => response.json())
        .then((item) => {
          this.items.push(item);
        });
    },
    UpdateCart(item) {
      this.precart.push(item);
      this.total += item.preco;
      localStorage.setItem("Cart", JSON.stringify(this.precart));
    },
    LoadCart() {
      if (localStorage.getItem("Cart") !== null) {
        this.precart = JSON.parse(localStorage.getItem("Cart"));
        this.precart.forEach((item) => {
          this.total += item.preco;
        });
      }
    },
    ClearItems() {
      this.precart = [];
      this.total = 0;
    },
  },
  mounted() {
    this.LoadCart();
    this.LoadAcougue();
    this.LoadPadaria();
    this.LoadHortifruti();
  },
};
</script>

<style>
.data-loading {
  padding: 5%;
}

.data {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  padding: 6%;
}

.adicionar {
  background-color: rgb(51, 204, 97);
  border-radius: 10px;
  color: white;
  border: 0;
}

.adicionar:hover {
  cursor: pointer;
}
</style>
