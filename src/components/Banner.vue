<script setup>
import { ref, onMounted } from "vue";
import axios from "axios";
import BannerSlide from "./BannerSlide.vue";
import BannerSwiper from "./BannerSwiper.vue";

const items = ref([]);

const handleBanner = (id) => {
  items.value.map((item) => {
    item.active = false;
    if (item.id === id) item.active = true;

    return item;
  });
};

onMounted(async () => {
  try {
    const response = await axios.get("http://localhost:4000/items");
    items.value = response.data;
  } catch (error) {
    console.error("Error fetching items", error);
  }
});
</script>

<style scoped>
.banner {
  position: relative;
  width: 100%;
  min-height: 90vh;
  background: var(--bgColor);
  transition: 1s;
}

@media (max-width: 768px) {
  .banner {
    min-height: 100vh;
  }
}
</style>

<template>
  <div class="banner">
    <BannerSlide v-for="item in items" :key="item.id" :item="item" />
    <BannerSwiper :items="items" :bannerChange="handleBanner" />
    <div>
      <p>Prashnta</p>
    </div>
  </div>
</template>

