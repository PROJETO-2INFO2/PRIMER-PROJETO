<script setup>
const produtos = [
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
];
</script>

<template>
  <header>
    <nav>
      <div class="logo">
        <img src="../src/components/image/B-World.png" alt="Logo" />
        <h1>Apreço a leitura</h1>
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
            <span class="fa-solid fa-cart-shopping"></span>
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
    <section>
      <div class="banner">
        <p>Autor de Abril</p>
        <h1>Eric-Emanuel Schmitt</h1>
        <p>
          Eric-Emmanuel Schmitt has been awarded more than 20 literary prizes and distinctions, and
          in 2001 he received the title of Chevalier des Arts et des Lettres. His books have been
          translated into over 40 languages.
        </p>
        <button>Acessar página do livro</button>
      </div>
      <img src="../src/components/image/book.png" alt="Banner" />
    </section>
    <section class="ofertas">
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
    <section class="Lancamentos">
      <h2>Lançamentos</h2>
      <div class="livros">
        <div v-for="produto in produtos" :key="produto.id" class="livro">
          <img :src="produto.capa" alt="Capa do livro" />
          <h3>{{ produto.titulo }}</h3>
          <p>{{ produto.resenha }}</p>
          <p>R$ {{ produto.preco.toFixed(2) }}</p>
          <button>Adicionar ao carrinho</button>
        </div>
      </div>
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
      <img src="image/VISA-card-logo- 1.png" alt="">
      <img src="image/MasterCard-Logo-1979 1.png" alt="">
      <img src="image/VISA-card-logo- 1.png" alt="">
    </div>
  </footer>
</template>

<style scoped>
</style>
