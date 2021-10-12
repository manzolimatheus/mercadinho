<template>
  <div class="container">
    <div class="form-container" v-show="show_form">
      <div class="form">
        <h1>Insira seus dados</h1>
        <form>
          <input
            type="text"
            placeholder="Nome completo"
            v-model="nome"
            required
            class="custom-input"
          />
          <br />
          <div>
            <input
              type="text"
              placeholder="Endereço completo"
              v-model="endereco"
              required
              class="custom-input"
            />
          </div>
          <div>
            <input
              type="text"
              placeholder="Ponto de referência (Opcional)"
              v-model="referencia"
              class="custom-input"
            />
          </div>
          <br />
          <div class="display: inline-block">
            <input
              type="checkbox"
              v-model="precisa_troco"
              required
              style="margin-right: 1%"
              @click="SwitchTroco"
            />
            <span>Precisa de troco?</span>
          </div>
          <br />
          <div v-show="precisa_troco">
            <label for="valor_a_pagar"
              >Digite a quantia que você entregará ao entregador quando ele
              chegar.</label
            >
            <br />
            R$
            <input
              type="number"
              v-model="valor_a_pagar"
              class="custom-input"
              step="0.01"
              :min="Number(this.preco.preco[0]).toFixed(2)"
              @input="GetTroco()"
            />
            <p class="mt">Você receberá R${{ troco.toFixed(2) }} de troco.</p>
          </div>
        </form>
      </div>
      <div class="map mt">
        <h1>Local</h1>
        <div class="mapouter">
          <div class="gmap_canvas">
            <iframe
              id="gmap_canvas"
              :src="`https://maps.google.com/maps?q=${endereco}&z=13&ie=UTF8&iwloc=&output=embed`"
              frameborder="0"
              scrolling="no"
              marginheight="0"
              marginwidth="0"
            ></iframe>
          </div>
        </div>
      </div>
      <div class="confirma mt">
        <h1>Confirme seus dados</h1>
        <div>
          <strong><ion-icon name="person"></ion-icon> Nome completo: </strong
          >{{ nome }}
        </div>
        <br />
        <div>
          <strong><ion-icon name="location"></ion-icon> Endereço: </strong
          >{{ endereco }}
        </div>
        <br />
        <div>
          <strong><ion-icon name="pin"></ion-icon> Refêrencia do local: </strong
          >{{ referencia }}
        </div>
      </div>
      <br />
      <button class="button-confirma" @click="NextStep()">
        Prosseguir <ion-icon name="arrow-forward-outline"></ion-icon>
      </button>
      <p v-show="msg">Preencha todos os campos para continuar</p>
    </div>
    <div class="full-info" v-show="show_info">
      <h1>
        Pague <strong>R${{ Number(this.preco.preco[0]).toFixed(2) }}</strong> ao
        entregador quando ele chegar, para receber seus produtos.
      </h1>
      <div class="animation-info">
        <lottie-player
          src="https://assets3.lottiefiles.com/packages/lf20_jmejybvu.json"
          background="transparent"
          speed="1"
          loop
          autoplay
        ></lottie-player>
        <div class="info">
          <h1>Obrigado pela preferência!</h1>
          <h2>Tempo de espera médio: 1h</h2>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FormFinal",
  data() {
    return {
      nome: null,
      endereco: null,
      referencia: null,
      precisa_troco: false,
      valor_a_pagar: 0,
      troco: 0,
      show_form: true,
      show_info: false,
      msg: false,
    };
  },
  props: {
    preco: Number,
  },
  methods: {
    NextStep() {
      if (this.nome !== null && this.endereco !== null) {
        this.show_form = false;
        this.show_info = true;
        this.PostData();
      } else {
        this.msg = true;
      }
    },
    async PostData() {
      fetch("http://localhost:3000/pedidos", {
        method: "post",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          nome: this.nome,
          endereco: this.endereco,
          referencia: this.referencia,
          valor_compra: Number(this.preco.preco[0]).toFixed(2),
          troco: this.troco.toFixed(2),
          pedido: JSON.parse(localStorage.getItem("Cart")),
          status: "Coletando pedido",
        }),
      }).then((response) => {
        console.log(response);
        localStorage.removeItem("Cart");
      });

      const user = {
        nome: this.nome,
        endereco: this.endereco,
        referencia: this.referencia,
      };

      localStorage.setItem("Auth", JSON.stringify(user));
    },
    SwitchTroco() {
      this.troco = 0;
      this.valor_a_pagar = 0;
      this.precisa_troco = !this.precisa_troco;
    },
    GetTroco() {
      this.troco = this.valor_a_pagar - Number(this.preco.preco[0]).toFixed(2);
    },
  },
  mounted() {
    this.nome = JSON.parse(localStorage.getItem('Auth')).nome;
    this.endereco = JSON.parse(localStorage.getItem('Auth')).endereco;
    this.referencia = JSON.parse(localStorage.getItem('Auth')).referencia;
  },
};
</script>

<style scoped>
.form-container {
  text-align: center;
}

.custom-input {
  margin-top: 1%;
  padding: 1%;
  border: 2px solid grey;
  border-radius: 10px;
  width: 50%;
}

iframe {
  width: 50%;
}

.mt {
  margin-top: 2%;
}

.confirma {
  display: grid;
  justify-content: center;
  text-align: justify;
}

.button-confirma {
  background-color: #36bd5e;
  padding: 1%;
  font-size: 18pt;
  color: white;
  border: 0;
  border-radius: 10px;
  width: 50%;
}

.full-info {
  text-align: center;
}

.full-info h1 {
  font-weight: 300;
}

.animation-info {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  justify-content: center;
  align-items: center;
}

.animation-info lottie-player {
  width: 100%;
}
</style>