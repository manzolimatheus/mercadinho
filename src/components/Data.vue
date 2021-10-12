<template>
  <div class="items">
    <FaixaCarrinho
      :cart="precart"
      :total="total"
      :show_buttons="true"
      @empty-cart="ClearItems"
    />
    <div class="data-loading">
      <div class="items-data">
        <h1>Items</h1>
        <hr />
        <div class="data">
          <div v-for="item in items[0]" :key="items.indexOf(item)">
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
      query: "http://localhost:3000/itens",
      categorias: [],
    };
  },
  methods: {
    async LoadData() {
      fetch(this.query)
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
    this.LoadData();
  },
};
</script>

<style>
.data {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  padding: 6%;
}

.items-data {
  padding: 3%;
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

@media (max-width: 768px) {
  .data {
    padding: 0;
    grid-template-columns: 50% 50%;
  }

  .imagem {
    width: 100%;
    height: auto;
  }
}
</style>
