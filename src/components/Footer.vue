<template>
  <div id="footer">
    <footer>
      <div class="apresentacao">
        <h3><ion-icon name="pricetags-outline"></ion-icon> Mercado São Miguel Arcanjo</h3>
        <q>Trazendo o melhor para sua mesa!</q>
      </div>
      <div class="links">
          <h3><ion-icon name="key-outline"></ion-icon> Acesso rápido</h3>
        <router-link to="/">Início</router-link>
        <br>
        <router-link to="/about">Sobre</router-link>
      </div>
      <div class="localizacao">
          <h3><ion-icon name="location-outline"></ion-icon> Venha conhecer</h3>
          <p>R. Agenos Carreiro, 173 - Jardim Suecia, Mogi Guaçu - SP, 13848-510</p>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: "Footer",
};
</script>

<style>
footer {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  background-color: #f3f3f3;
  padding: 5%;
}

footer a{
  color: #272727;
}

@media (max-width: 768px){
  footer{
    grid-template-columns: 100%;
  }
}
</style>