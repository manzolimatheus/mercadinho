<template>
  <div id="navbar">
    <header>
      <img src="/img/logo-mercado.png" alt="Logo São Miguel Arcanjo" />
    </header>
    <nav>
      <div class="links">
        <router-link to="/"
          ><ion-icon name="home-outline"></ion-icon> Início</router-link
        >
        <router-link to="/about"
          ><ion-icon name="flower-outline"></ion-icon> Sobre</router-link
        >
        <router-link to="/items"
          ><ion-icon name="gift-outline"></ion-icon> Itens</router-link
        >
        <router-link to="/cart"
          ><ion-icon name="cart-outline"></ion-icon> Carrinho</router-link
        >
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  name: "Navbar"
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

#navbar {
  background-color: #3cdb84;
  padding: 1%;
  text-align: center;
}

h2 {
  color: #11522e;
}

nav {
  margin-top: 1%;
  text-align: center;
}

nav a {
  color: white;
  text-decoration: none;
  padding-inline: 1%;
  font-weight: 500;
}

nav a:hover {
  color: #1e7444;
}

.logo img {
  width: 100px;
}

.bt-carrinho {
  background-color: white;
  color: #35c776;
  border-radius: 10px;
  padding: 1%;
}
</style>