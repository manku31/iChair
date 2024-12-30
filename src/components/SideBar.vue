<script setup>
import { scisData } from "@/data/scisData";
import SideMenu from "@/components/SideMenu.vue";
import { ref } from "vue";

const scis = ref(scisData);
const active = ref(false);

const handleToggleMenu = () => {
  active.value = !active.value;
};
</script>

<style scoped>
.sideBar {
  position: fixed;
  width: 5%;
  min-height: 100vh;
  padding: 30px;
  background: var(--primary);
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-direction: column;
  transition: 1s;
  z-index: 2000;
}

.menu {
  font-size: 1.6rem;
  color: #000000;
  z-index: 2000;
  transition: ease 1s;
}

.menu.active {
  transform: rotateZ(180deg);
}

.sci {
  padding: 0;
  display: inline-flex;
  justify-content: flex-start;
  align-items: center;
  flex-direction: column;
  gap: 25px;
}

.sci li {
  list-style: none;
}

.sci li a {
  font-size: 1.6rem;
  color: #000000;
}
</style>

<template>
  <div class="sideBar">
    <a
      class="menu"
      :class="{ active: active }"
      @click.stop.prevent="handleToggleMenu"
    >
      <i class="bi bi-arrow-right-circle-fill" />
    </a>
    <ul class="sci">
      <li v-for="sci in scis" :key="sci.id">
        <a href="#">
          <i :class="sci.icon" />
        </a>
      </li>
    </ul>
  </div>
  <SideMenu :active="active" />
</template>
