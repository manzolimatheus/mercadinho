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
          />
          <br />
          <div>
            <input
              type="text"
              placeholder="Endereço completo"
              v-model="endereco"
              required
            />
          </div>
          <br />
          <input
            type="text"
            placeholder="Ponto de referência (Opcional)"
            v-model="referencia"
          />
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
    <div class="pix" v-show="show_pix">
      <p>Pague <strong>R${{ preco.preco }}</strong> através desse código PIX para podermos confirmar seu pedido.</p>
      <img src="/img/qrcode-pix.png" alt="Código pix para pagar" />
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
      show_form: true,
      show_pix: false,
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
        this.show_pix = true;
        this.PostData()
      } else {
        this.msg = true;
      }
    },
    async PostData(){
      fetch('http://localhost:3000/pedidos', {
        method: 'post',
        headers:{
           'Content-Type': 'application/json'
        },
        body: JSON.stringify({
          nome: this.nome,
          endereco: this.endereco,
          referencia: this.referencia,
          pedido: JSON.parse(localStorage.getItem('Cart'))
        })
      })
      .then(response => {
        console.log(response)
        localStorage.removeItem("Cart")
      })
    }
  },
};
</script>

<style scoped>
.form-container {
  text-align: center;
}

input {
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

.pix{
  text-align: center;
}
</style>