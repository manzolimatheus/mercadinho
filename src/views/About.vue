<template>
  <div class="about">
    <div class="sobre-nos">
      <h1 data-aos="zoom-in">Sobre nós</h1>
      <h2 data-aos="zoom-in">Trazendo qualidade e confiança para sua mesa desde 2019!</h2>
    </div>
    <div class="destaque">
      <h1 data-aos="fade-right">Nossos três pilares</h1>
      <br>
      <div class="colunas">
        <div data-aos="zoom-out">
          <img
            src="https://images.unsplash.com/photo-1541557435984-1c79685a082b?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=870&q=80"
            alt="Funcionário montando lanche"
          />
          <h3>
            <ion-icon name="ribbon-outline"></ion-icon> O melhor atendimento
          </h3>
          <p>
            Buscamos sempre o melhor atendimento para o cliente, conte conosco
            para tudo!
          </p>
        </div>
        <div data-aos="zoom-out">
          <img
            src="https://images.unsplash.com/photo-1560249956-b3731ecf3153?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=870&q=80"
            alt="Homem trabalhando feliz"
          />
          <h3>
            <ion-icon name="heart-outline"></ion-icon> Aqui trabalhamos com amor
          </h3>
          <p>Trabalhamos dando tudo de si para tornar seu dia mais gostoso!</p>
        </div>
        <div data-aos="zoom-out">
          <img
            src="https://images.unsplash.com/photo-1544986581-efac024faf62?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=870&q=80"
            alt="Garçom servindo bebida cara"
          />
          <h3>
            <ion-icon name="star-outline"></ion-icon> Para nós todo cliente é
            VIP
          </h3>
          <p>
            Para nós, todos são iguais! Pessoas com fome que desejam um lugar
            confortável e comida gostosa!
          </p>
        </div>
      </div>
    </div>
    <div class="jobs fix">
      <br>
      <h1 data-aos="fade-right">Quer trabalhar conosco?</h1>
      <div class="duas-colunas">
        <div data-aos="zoom-out">
          <lottie-player
            src="https://assets9.lottiefiles.com/packages/lf20_hQXKtu.json"
            background="transparent"
            speed="1"
            style="width: 80%"
            loop
            autoplay
          ></lottie-player>
        </div>
        <div>
          <h1 data-aos="zoom-in">Há várias vagas disponíveis, vem ver se dá match!</h1>
        </div>
      </div>
    </div>
    <div class="fix">
      <h1 data-aos="fade-right">Venha nos encontrar</h1>
      <br>
      <div class="duas-colunas">
        <div>
          <h1 data-aos="fade-right">Venha visitar o melhor mercado da região!</h1>
        </div>
        <div>
          <iframe
            id="gmap_canvas"
            src="https://maps.google.com/maps?q=R. Agenos Carreiro, 173 - Jardim Suecia, Mogi Guaçu - SP, 13848-510&z=13&ie=UTF8&iwloc=&output=embed"
            frameborder="0"
            scrolling="no"
            style="width: 100%; height: 100%"
            marginheight="0"
            marginwidth="0"
            data-aos="zoom-out"
          ></iframe>
        </div>
      </div>
      <br>
    </div>
  </div>
</template>

<style scoped>
.sobre-nos {
  background-color: #29d183;
  padding: 1%;
  text-align: center;
}

.destaque{
  margin-top: 3%;
  text-align: center;
}

.colunas {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
}

.colunas h3 {
  text-align: center;
}

.colunas p {
  padding: 5%;
}

.colunas img {
  width: 100%;
}

.jobs {
  background-color: blueviolet;
  color: white;
}

.fix {
  text-align: center;
  padding: 1%;
  margin-top: 3%;
}

.duas-colunas {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}

.duas-colunas h1 {
  padding: 10%;
}
</style>
