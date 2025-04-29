<script setup>
import { ref } from "vue";
const produtos = ref([
    {
        id: 1,
        titulo: 'Chain of Iron: Volume 2',
        resenha: 'Cassandra Clare',
        preco: 23.24,
        capa: '../src/components/image/1.png',
    },
    {
        id: 2,
        titulo: 'Chain of Thorns',
        resenha: 'Cassandra Clare',
        preco: 23.24,
        capa: '../src/components/image/2.png',
    },
    {
        id: 3,
        titulo: 'City of Fallen Angels',
        resenha: 'Cassandra Clare',
        preco: 13.94,
        capa: '../src/components/image/3.png',
    },
    {
        id: 4,
        titulo: 'Nona the Ninth',
        resenha: 'Cassandra Clare',
        preco: 16.84,
        capa: '../src/components/image/4.png',
    },
    {
        id: 5,
        titulo: 'Harlem Shuffle',
        resenha: 'Cassandra Clare',
        preco: 26.92,
        capa: '../src/components/image/5.png',
    },
    {
        id: 6,
        titulo: 'Two Old Women',
        resenha: 'Colson Whitehead',
        preco: 13.95,
        capa: '../src/components/image/6.png',
    },
    {
        id: 7,
        titulo: 'Carrie Soto Is Back',
        resenha: 'Taylor Jenkins Reid',
        preco: 26.04,
        capa: '../src/components/image/7.png',
    },
    {
        id: 8,
        titulo: 'Book Lovers',
        resenha: 'Emily Henry',
        preco: 15.81,
        capa: '../src/components/image/8.png',
    }
]);
const carrinho = ref([]);
const mostrarCarrinho = ref(false)
function adicionarAoCarrinho(index) {
  carrinho.value.push(produtos.value[index])
}
</script>

<template>
  <header>
    <nav>
      <div class="logo">
        <img src="../src/components/image/B-World.png" alt="Logo" />
        <p>Apreço a leitura</p>
      </div>

      <form action="/buscar" method="GET">
        <input type="text" name="q" placeholder="Pesquisar..." />
        <button type="submit">Buscar</button>
      </form>

      <ul>
        <li>
          <a href="#">Termos</a>
        </li>
        <li>
          <a href="#">Equipe</a>
        </li>
        <li>
          <a href="#">Envio</a>
        </li>
        <li>
          <a href="#">Devoluções</a>
        </li>
      </ul>

      <div>
        <ul>
          <li>
            <span @click="mostrarCarrinho = !mostrarCarrinho" class="fa-solid fa-cart-shopping"></span>
          </li>
          <li>
            <span class="fa-solid fa-heart"></span>
          </li>
          <li>
            <span class="fa-solid fa-user"></span>
          </li>
        </ul>
      </div>
    </nav>
  </header>

  <main>
    <section class="banner" v-if="!mostrarCarrinho">
      <div class="ban">
        <div class="texto">
          <p>Autor de Abril</p>
        <h1>Eric-Emanuel Schmitt</h1>
        <p>
          Eric-Emmanuel Schmitt has been awarded more than 20 literary prizes and distinctions, and
          in 2001 he received the title of Chevalier des Arts et des Lettres. His books have been
          translated into over 40 languages.
        </p>
        <button>Acessar página do livro</button>
        </div>
      <div>
        <img src="../src/components/image/book.png" alt="Banner" />
      </div>
    </div>
    </section>
    <section class="ofertas" v-if="!mostrarCarrinho">
      <div class="frete">
        <span class="fa-solid fa-truck"></span>
        <p>Frete grátis para SC</p>
      </div>
      <div class="recomendados">
        <span class="fa-solid fa-star"></span>
        <p>Livros recomendados</p>
      </div>
      <div class="vendidos">
        <span class="fa-solid fa-book-open"></span>
        <p>Mais vendidos</p>
      </div>
    </section>
    <section class="Lancamentos" v-if="!mostrarCarrinho">
      <h2>Lançamentos</h2>
      <div class="livros">
        <div v-for="(item, index) of produtos" :key="index" class="livro">
          <img :src="item.capa" alt="Capa do livro" />
          <h3>{{ item.titulo }}</h3>
          <p>{{ item.resenha }}</p>
          <p>R$ {{ item.preco.toFixed(2) }}</p>
          <button @click="adicionarAoCarrinho(index)">Adicionar ao carrinho</button>
        </div>
      </div>
    </section>
    <section class="carrinho" v-if="mostrarCarrinho">
      <ul>
        <li v-for="(item, index) of carrinho">
          <img :src="item.capa" alt="capa">

        </li>
      </ul>
      <h2>Carrinho</h2>
    </section>
  </main>

  <footer>
    <div>
      <p>IFbooks</p>
      <span class="fa-brands fa-square-facebook"></span>
      <span class="fa-brands fa-square-instagram"></span>
      <span class="fa-brands fa-square-twitter"></span>
    </div>
    <div>
      <p>Contato</p>
      <span class="fa-solid fa-phone"></span><p>+55 47 40045263</p>
      <span class="fa-solid fa-clock"></span><p>8h às 23h - Seg a Sex</p>
      <span class="fa-solid fa-envelope"></span><p>contato@ifbooks.com</p>

      <img src="../src/components/image/paipal 1.png" alt="">
      <img src="../src/components/image/MasterCard-Logo-1979 1.png" alt="">
      <img src="../src/components/image/VISA-card-logo- 1.png" alt="">
    </div>
  </footer>
</template>

<style scoped>
  * {
    margin: 0 20px;
    padding: 0;
    box-sizing: border-box;
  }
  body {
    background-color: #F1F1F1;
    color: #231F2D;
  }
  header {
    justify-content: space-between;
    align-items: center;
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif
  }

  nav {
    margin: 0 20px;
    display: flex;
    align-items: center;
  }

  .logo {
    display: flex;
    align-items: center;
    color: #27AE60;
  }

  .logo img {
    width: 50px;
    height: auto;
    margin-right: 10px;
  }

  form {
    align-items: center;
    margin-left: auto;
  }

  form input[type="text"] {
    border-radius: 1px;
    border: 4px solid #F1F1F1;
    background-color: #F1F1F1;
  }

  form button {
    border-radius: 1px;
    border: 4px solid #F1F1F1;
    background-color: #F1F1F1;
    color: #231F2D;
    cursor: pointer;
  }

  ul {
    list-style-type: none;
    display: flex;
    margin-left: auto;
  }

  ul li {
    margin: 0;
  }
  ul li a {
    text-decoration: none;
    color: #231F2D;
    margin: 0 10px;
  }
  ul li a:hover {
    color: #27AE60;
  }
  ul li span {
    font-size: 20px;
    margin: 0 10px;
    cursor: pointer;
  }
  ul li span:hover {
    color: #27AE60;
  }
  main {
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif
  }
  .banner {
    justify-content: space-between;
    align-items: center;
    margin: 20px 20px;
    padding: 30px 10px;
  }
  .ban {
    display: flex;
  }
  .ban div img {
    width: auto;
    height: 80%;
  }
  .ban .texto {
    font-size: 20px;
    padding: 0 10px;
  }
  .ban .texto p {
    padding: 5px 0 5px 0;
  }
  .ban h1 {
    font-size: 40px;
    color: #231F2D;
  }
  .ban button {
    background-color: #27AE60;
    color: #F1F1F1;
    border: none;
    padding: 10px 20px;
    border-radius: 2px;
    cursor: pointer;
  }
  .ban button:hover {
    background-color: #1E7A50;
  }
</style>
