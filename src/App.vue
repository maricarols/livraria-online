<script setup>
import { ref } from "vue";
let pesquisando = ref(``);
function limpar() {
  pesquisando.value = ``;
}
</script>

<template>
     <header>
      <div class="logo">
        <a href="index.html">
          <img src="../public/images/logo.png" alt="">
        </a>
      </div>
      <div class="pesquisa">
        <input type="text" placeholder="Pesquisar" v-model="pesquisando">
        <span class="fa-solid fa-magnifying-glass" style="color: #ca8e82;" @click="limpar"></span>
      </div>
      <ul class="menu">
        <li>Termos</li>
        <li>Equipe</li>
        <li>Envio</li>
        <li>Devoluções</li>
        <li>
          <a href="#">
            <span class="fa-solid fa-cart-shopping"></span>
          </a>
        </li>
        <li class="coracao">
          <a href="#">
            <span class="fa-solid fa-heart"></span>
          </a>
        </li>
        <li>
          <a href="#">
            <span class="fa-solid fa-user"></span>
          </a>
        </li>
      </ul>
    </header>
</template>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0vw 0 0 0;
  border-bottom: #f2d6ce solid 1px;
  padding-bottom: 2vw;

}

div.logo {
  margin-left: 3vw;
  margin-top: 1vw;
}

.logo img {
  height: 6vw;
  width: 6vw;
  border-radius: 100%;
}

header ul {
  display: flex;
  margin: 0 6vw 0 0;
}

header li {
  margin: 0 2vw;
}

header li p {
  color: #292421;
}

input {
  border: none;
  background-color: #f2d6ce;
  padding: 0.5vw 10vw 0.5vw 0.5vw;
  outline: none;
  font-family: "Nunito", sans-serif;
  color: #ca8e82;
}

input::placeholder {
  color: #ca8e82;
  font-family: "Nunito", sans-serif;
}

div.pesquisa {
  display: flex;
  align-items: center;
  background-color: #f2d6ce;
  padding: 0 1vw;
  border-radius: 10vw;
  margin: 0 2vw 0 3vw;
}

li span {
  font-size: 1vw;
}

li.coracao span {
  border-right: #f2d6ce solid 2px;
  border-left: #f2d6ce solid 2px;
  padding: 0 2vw 0 2vw;
}
header li span {
  color: #ca8e82;
}

header li:hover span {
  color: #a07168;

}

header li:hover {
  color: #a16e6e;
  cursor: pointer;
}

header span:hover {
  color: #a16e6e;
  cursor: pointer;
}

</style>
