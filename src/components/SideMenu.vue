<template>
  <div class="side-menu" :class="{ active: active }">
    
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
  </div>
</template>

<script setup>
import { ref } from "vue";
import { navsData } from "@/data/navData";

const props = defineProps({
  active: {
    type: Boolean,
    required: true,
  },
});

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
.side-menu {
  position: fixed;
  left: -300px;
  width: 300px;
  height: 100%;
  padding: 30px;
  background: var(--primary);
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-direction: column;
  transition: 1s;
  z-index: 1000;
}

.side-menu.active {
  left: 0;
}

.side-menu .nav {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 25px;
}

.nav li {
  list-style: none;
  margin: 0 10px;
}

.nav li a {
  color: #000000;
  text-decoration: none;
  font-weight: 600;
  letter-spacing: 2px;
  cursor: pointer;
  transition: 0.3s;
}

.nav li:hover a,
.nav li a.active {
  color: var(--third);
}
</style>
