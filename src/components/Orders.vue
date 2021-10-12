<template>
  <div class="pedidos">
    <div class="vazio" v-if="this.pedidos.length < 1">
      <p>Você ainda não fez nenhum pedido.</p>
    </div>
    <div class="div-pedidos" v-else>
      <div class="usuario">
        <img
          :src="`https://ui-avatars.com/api/?name=${this.nome}&color=7F9CF5&background=EBF4FF`"
          alt=""
        />
        <h3>{{ this.nome }}</h3>
      </div>
      <hr />
      <div class="meus-pedidos">
        <h3>
          <ion-icon name="fast-food-outline"></ion-icon> Meus pedidos ({{
            this.pedidos[0].length
          }})
        </h3>
        <br />
      </div>
      <div class="table">
        <table>
          <thead>
            <th>#</th>
            <th><ion-icon name="location"></ion-icon> Endereço</th>
            <th><ion-icon name="pin"></ion-icon> Referência</th>
            <th><ion-icon name="list"></ion-icon> Pedido</th>
            <th><ion-icon name="cash"></ion-icon> Valor</th>
            <th><ion-icon name="wallet"></ion-icon> Troco</th>
            <th><ion-icon name="cog"></ion-icon> Status</th>
          </thead>
          <tbody>
            <tr v-for="pedido in pedidos[0]" :key="pedido.id">
              <td>{{ pedido.id }}</td>
              <td>{{ pedido.endereco }}</td>
              <td>{{ pedido.referencia }}</td>
              <td>
                <select>
                  <option v-for="item in pedido.pedido" :key="item.id">
                    {{ item.nome }} - R${{ item.preco }}
                  </option>
                </select>
              </td>
              <td>{{ pedido.valor_compra }}</td>
              <td>{{ pedido.troco }}</td>
              <td>{{ pedido.status }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Pedidos",
  data() {
    return {
      nome: null,
      pedidos: [],
    };
  },
  methods: {
    async LoadData() {
      fetch(`http://localhost:3000/pedidos?nome=${this.nome}`)
        .then((response) => response.json())
        .then((data) => {
          this.pedidos.push(data);
        });
    },
  },
  mounted() {
    this.nome = JSON.parse(localStorage.getItem("Auth")).nome;
    this.LoadData();
  },
};
</script>

<style>
.usuario {
  display: inline-flex;
  line-height: 100px;
  width: 100%;
}

.usuario h3 {
  font-size: large;
  padding-left: 1%;
}

.usuario img {
  clip-path: circle();
}

.meus-pedidos {
  margin-top: 5%;
}

.pedidos {
  padding: 5%;
  height: 70vh;
}

.table{
  overflow-x: auto;
}

table {
  width: max-content;
}

table th {
  text-align: left;
}

table select {
  width: 100%;
}

@media (min-width: 768px){
  table{
    width: 100%;
  }
}
</style>