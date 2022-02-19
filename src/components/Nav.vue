<script setup lang="ts">

</script>

<template>
  <div class="logo" />
  <nav mt-18 mb-24>
    <router-link class="icon-btn mx-2" to="/posters" title="海报">
      海报
    </router-link>
    <router-link class="icon-btn mx-2" to="/" title="海报">
      字体
    </router-link>
    <router-link class="icon-btn mx-2" to="/videos" title="海报">
      视频
    </router-link>
    <router-link class="icon-btn mx-2" to="/" title="海报">
      公众号
    </router-link>
  </nav>
</template>

<style>
.logo {
  width: 60px;
  height: 60px;
  background-color: #ccc;
  margin: 0 auto;
}
nav {
  display: flex;
  justify-content: space-around;
  width: 400px;
  margin: 0 auto;
  color: #333;
}
</style>
