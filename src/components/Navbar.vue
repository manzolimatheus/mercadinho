<template>
  <div id="navbar">
    <header>
      <img src="/img/logo-mercado.png" alt="Logo São Miguel Arcanjo" />
    </header>
    <!-- Nav pc -->
    <nav class="nav-pc">
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
        <router-link to="/orders"
          ><ion-icon name="arrow-redo-outline"></ion-icon> Meus pedidos</router-link
        >
      </div>
    </nav>
    <!-- Nav mobile -->
    <nav class="nav-mobile">
      <button @click="showNavMobile"><ion-icon name="menu"></ion-icon></button>
      <div class="links-mobile" id="links_mobile">
        <router-link to="/"
          ><ion-icon name="home-outline"></ion-icon> Início</router-link
        >
        <br>
        <router-link to="/about"
          ><ion-icon name="flower-outline"></ion-icon> Sobre</router-link
        >
        <br>
        <router-link to="/items"
          ><ion-icon name="gift-outline"></ion-icon> Itens</router-link
        >
        <br>
        <router-link to="/cart"
          ><ion-icon name="cart-outline"></ion-icon> Carrinho</router-link
        >
        <br>
        <router-link to="/orders"
          ><ion-icon name="arrow-redo-outline"></ion-icon> Meus pedidos</router-link
        >
        <br>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  name: "Navbar",
  methods:{
    showNavMobile(){
      const links = document.getElementById('links_mobile').style
      
      if (links.display === 'none'){
        links.display = 'block'
      }else{
        links.display = 'none'
      }
    }
  }
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

.links-mobile{
  text-align: justify;
  font-size: large;
  display: none;
}

@media (min-width:768px){
  .nav-pc{
    display: block;
  }

  .nav-mobile{
    display: none;
  }
}

@media (max-width:768px){
  .nav-pc{
    display: none;
  }

  .nav-mobile{
    display: block;
    text-align: right;
  }

}

</style>