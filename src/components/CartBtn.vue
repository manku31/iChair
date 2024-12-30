<script setup></script>

<style scoped>
.cart-btn {
  display: flex;
  align-items: center;
  gap: 10px;
  transition: 0.5s;
}

.cart {
  font-size: 30px;
  color: #ffffff;
  position: relative; /* Add this */
}

.count {
  font-size: 1.2rem;
  color: #ffffff;
  width: 30px;
  height: 30px;
  padding: 5px;
  border-radius: 50%;
  background: #00a950;
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute; /* Add this */
  top: 7px; /* Add this */
  right: -37px; /* Add this */
}
</style>

<template>
  <div class="cart-btn">
    <RouterLink to="/cart" class="cart">
      <i class="bi bi-cart2" />
      <span class="count">3</span>
    </RouterLink>
  </div>
</template>
