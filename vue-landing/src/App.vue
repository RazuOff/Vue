<template>
  <div>
    <!-- Хедер -->
    <header class="header">
      <h1>Кофейня "Арома"</h1>
      <nav>
        <a href="#hero">Главная</a>
        <a href="#about">О нас</a>
        <a href="#menu">Меню</a>
        <a href="#gallery">Галерея</a>
        <a href="#contact">Контакты</a>
      </nav>
    </header>

    <!-- Баннер -->
    <section id="hero" class="hero">
      <h2>Добро пожаловать в наш мир кофе</h2>
      <p>Наслаждайся ароматом каждое утро ☕</p>
    </section>

    <!-- О нас -->
    <section id="about" class="section">
      <h2>О нас</h2>
      <p>
        Мы — команда энтузиастов, открывшая кофейню из любви к настоящему кофе. Наша миссия — создавать атмосферу уюта, где каждый может отдохнуть и насладиться вкусом свежесваренного кофе.
      </p>
    </section>

    <!-- Меню -->
    <section id="menu" class="section alt">
      <h2>Меню</h2>
      <div class="menu-list">
        <div v-for="item in menuItems" :key="item.name" class="menu-item">
          <h3>{{ item.name }}</h3>
          <p>{{ item.description }}</p>
          <span>{{ item.price }}₽</span>
        </div>
      </div>
    </section>

    <!-- Галерея -->
    <section id="gallery" class="section">
      <h2>Галерея</h2>
      <div class="gallery">
        <img src="/src/assets/coffee1.png" alt="Кофе 1" />
        <img src="/src/assets/coffee2.png" alt="Кофе 2" />
        <img src="/src/assets/coffee3.png" alt="Кофе 3" />
      </div>
    </section>

    <!-- Контакты -->
    <section id="contact" class="section alt">
      <h2>Обратная связь</h2>
      <form @submit.prevent="submitForm" class="form">
        <input type="text" v-model="form.name" placeholder="Ваше имя" required />
        <input type="email" v-model="form.email" placeholder="Email" required />
        <textarea v-model="form.message" placeholder="Сообщение" required></textarea>
        <button type="submit">Отправить</button>
      </form>
      <p v-if="submitted" class="success">Спасибо за сообщение!</p>
    </section>

    <!-- Подвал -->
    <footer class="footer">
      &copy; 2025 Кофейня "Арома"
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const menuItems = [
  {
    name: 'Эспрессо',
    description: 'Крепкий и насыщенный — идеальный старт дня.',
    price: 150,
  },
  {
    name: 'Капучино',
    description: 'Классика с воздушной пенкой.',
    price: 200,
  },
  {
    name: 'Латте',
    description: 'Мягкий вкус с нотками ванили.',
    price: 220,
  },
  {
    name: 'Флэт Уайт',
    description: 'Сбалансированный вкус эспрессо и молока.',
    price: 230,
  },
]

const form = ref({
  name: '',
  email: '',
  message: '',
})

const submitted = ref(false)

function submitForm() {
  console.log(form.value)
  submitted.value = true
  setTimeout(() => {
    submitted.value = false
    form.value = { name: '', email: '', message: '' }
  }, 3000)
}
</script>

<style scoped>
body {
  font-family: 'Segoe UI', sans-serif;
  margin: 0;
  background-color: white;
  scroll-behavior: smooth;
}

.header {
  background-color: #6b4f4f;
  color: white;
  padding: 1rem;
  text-align: center;
  position: sticky;
  top: 0;
  z-index: 1000;
}

.header nav a {
  color: white;
  margin: 0 12px;
  text-decoration: none;
  font-weight: bold;
}

.hero {  
  background-color: #6b4f4f;
  color: white;
  padding: 6rem 2rem;
  text-align: center;
}

.section {
  color: #6b4f4f;
  padding: 3rem 2rem;
  background-color: #fffaf3;
}

.section.alt {
  background-color: #f8efe0;
}

.menu-list {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 1.5rem;
}

.menu-item {
  border: 1px solid #ccc;
  padding: 1rem;
  border-radius: 8px;
  background: white;
  transition: transform 0.2s;
}

.menu-item:hover {
  transform: scale(1.02);
}

.gallery {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  justify-content: center;
}

.gallery img {
  width: 200px;
  height: auto;
  border-radius: 8px;
}

.form {
  
  display: flex;
  flex-direction: column;
  max-width: 400px;
  margin: auto;
}

.form input,
.form textarea {
  margin-bottom: 1rem;
  padding: 0.5rem;
  border-radius: 6px;
  border: 1px solid #ccc;
}

.form button {
  background-color: #6b4f4f;
  color: white;
  padding: 0.7rem;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}

.success {
  text-align: center;
  color: green;
  margin-top: 1rem;
}

.footer {
  background-color: #6b4f4f;
  color: white;
  text-align: center;
  padding: 1rem;
}
</style>
