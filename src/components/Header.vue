<template>
  <header id="home">
    <RouterLink to="/" class="logo">iChair</RouterLink>
    <ul class="nav">
      <li v-for="nav in navs" :key="nav.id">
        <RouterLink
          v-if="nav.name === 'Home'"
          to="/"
          :class="{ active: nav.active }"
          @click="handleNavActive(nav.id)"
        >
          <i class="bi bi-house-door-fill" />
        </RouterLink>
        <RouterLink
          v-else
          to="/"
          :class="{ active: nav.active }"
          @click="handleNavActive(nav.id)"
          >{{ nav.name }}</RouterLink
        >
      </li>
    </ul>
    <div class="features">
      <CartBtn />
    </div>
  </header>
</template>

<script setup>
import { navsData } from "@/data/data";
import { ref } from "vue";
import CartBtn from "@/components/CartBtn.vue";

const navs = ref(navsData);

const handleNavActive = (id) => {
  navs.value.map((nav) => {
    nav.active = false;

    if (nav.id === id) nav.active = true;
    return nav;
  });
};
</script>

<style scoped>
header {
  position: relative;
  width: 95%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 30px 100px 30px 200px;
  z-index: 1100;
}

.logo {
  font-size: 35px;
  color: #fff;
  letter-spacing: 2px;
  font-weight: 800;
}

.nav {
  display: flex;
}

.nav li {
  list-style: none;
  margin: 0 10px;
}

.nav li a {
  color: #ffffff;
  text-decoration: none;
  font-weight: 600;
  letter-spacing: 2px;
  cursor: pointer;
  transition: 0.3s;
}

.nav li:hover a,
.nav li a.active {
  color: var(--primary);
}

.features {
  display: flex;
  align-items: center;
  gap: 10px;
}

@media (max-width: 768px) {
  header {
    padding: 10px 50px;
  }
  .nav {
    display: none;
  }
}
</style>
