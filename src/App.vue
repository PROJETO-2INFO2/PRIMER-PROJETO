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
            <div class="div">
              <span @click="mostrarCarrinho = !mostrarCarrinho" class="fa-solid fa-cart-shopping"></span>
            </div>
          </li>
          <li>
            <div class="div">
              <span class="fa-solid fa-heart"></span>
            </div>
          </li>
          <li>
           <div>
            <span class="fa-solid fa-user"></span>
           </div>
          </li>
        </ul>
      </div>
    </nav>
  </header>

  <main>
    <section class="banner" v-if="!mostrarCarrinho">
      <div class="ban">
        <div class="texto">
          <p class="pverde">Autor de Abril</p>
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
        <li>
          <h2>Carrinho de Compras</h2>
          <span @click="mostrarCarrinho = false" class="fa-solid fa-xmark"></span>
        </li>
      </ul>
      <ul>
        <li v-for="(item, index) of carrinho">
          <img :src="item.capa" alt="capa">
          <h3>{{ item.titulo }}</h3>
          <p>{{ item.resenha }}</p>
          <p>R$ {{ item.preco.toFixed(2) }}</p>
          <button @click="carrinho.splice(index, 1)">Remover</button>
        </li>
      </ul>
      <h2>Total: R$ {{carrinho.reduce((total, item) => total + item.preco, 0).toFixed(2)}}</h2>
      <button @click="mostrarCarrinho = false">Finalizar compra</button>
      <button @click="carrinho = []">Limpar carrinho</button>
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
      <span class="fa-solid fa-phone"></span>
      <p>+55 47 40045263</p>
      <span class="fa-solid fa-clock"></span>
      <p>8h às 23h - Seg a Sex</p>
      <span class="fa-solid fa-envelope"></span>
      <p>contato@ifbooks.com</p>

      <img src="../src/components/image/paipal 1.png" alt="">
      <img src="../src/components/image/MasterCard-Logo-1979 1.png" alt="">
      <img src="../src/components/image/VISA-card-logo- 1.png" alt="">
    </div>
  </footer>
</template>

<style scoped>
header {
  border-bottom: solid #27AE60;
}

header nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0px 100px 0px 100px;
  text-align: center;
}

header nav div.logo {
  display: flex;
}

header nav div.logo p {
  border-left: solid #27AE60;
  flex-wrap: wrap;
  padding: 0px 10px;
  color: #27AE60;
}header nav div.logo img{
 width: 100%;
 left: 100%;
}
header nav ul {
  display: flex;
}
header nav ul li {
  padding: 0px 20px;
  list-style: none;
}

header nav ul li a {
  text-decoration: none;
  color:#7B7881;
  font-size:17px ;
}header nav ul li div.div span{
  color: #27AE60;
  font-size: 20px;
  border-right: solid #27AE60;
  padding:0px 25px 0px 0px;
}header nav ul li div span{
 color: #27AE60;
  font-size: 20px;
}section.banner div.ban {
display: flex;
}section.banner  p.pverde {
 color: #27AE60;
 border: solid#27AE60;
 padding: 10px;
 border-radius: 10px;
 flex-wrap: wrap;
}section.banner div.texto{
  margin: 100px;
}section.banner  div div h1{
  font-size: 45px;
}section.banner  div div p{
  color: #4D4C4C;
  font-size: 25px;
}section.banner  div div button{
  background: #27AE60;
  text-decoration: none;
  padding: 15px 25px;
  color: blanchedalmond;
  border: none;
}
/*=================
      ofertas      
===================*/
section.ofertas{
  display: flex;
  padding: 50px;
  border-bottom:solid#27AE60 ;
  border-top: solid#27AE60;
  justify-content: space-between;
  align-items: center;
}
section.ofertas div {
  margin: 50px;
  padding:0px 20px 0px 0px;
  display: flex;
  font-size: 30px;
  border-right:solid#27AE60 ;
}section.ofertas div span{
  padding: 29px 20px;
}section.ofertas div.vendidos{
  border: none;
}section.ofertas div p{
  padding:0px 20px
};

</style>
