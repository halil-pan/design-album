<script setup lang="ts">
const router = useRouter()
</script>

<template>
  <main class="layout-detail">
    <button class="btn-back" @click="router.back()">
      <svg width="1.4em" height="1.4em" viewBox="0 0 24 24"><path fill="currentColor" d="M16.88 2.88a1.25 1.25 0 0 0-1.77 0L6.7 11.29a.996.996 0 0 0 0 1.41l8.41 8.41c.49.49 1.28.49 1.77 0s.49-1.28 0-1.77L9.54 12l7.35-7.35c.48-.49.48-1.28-.01-1.77z" /></svg>
    </button>
    <router-view />
  </main>
</template>

<style>
.layout-detail {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 120px;
}
.btn-back {
  color: #333;
  position: fixed;
  top: 40px;
  left: 40px;
}
</style>
