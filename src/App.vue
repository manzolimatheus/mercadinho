<template>
  <Navbar/>
  <router-view/>
  <Footer/>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import Footer from "@/components/Footer.vue";

export default {
  name: 'App',
  components:{
    Navbar,
    Footer
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Fira+Sans+Condensed');
@import url('https://fonts.googleapis.com/css2?family=Roboto+Slab');

h1, h2, h3, h4, h5, h6, strong{
  font-family: 'Roboto Slab', serif;
}

*{
  font-family: 'Fira Sans Condensed', sans-serif;
}

a{
  text-decoration: none;
}

/* Scrollbar */

/* width */
::-webkit-scrollbar {
  width: 10px;
}

/* Track */
::-webkit-scrollbar-track {
  background: #f1f1f1;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: rgb(187, 187, 187);
  border-radius: 10px;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #555;
}

/* Cor Seleção */
::-moz-selection { /* Code for Firefox */
  background: #37c276;
}
</style>