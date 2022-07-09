<template>
  <div class="container">
    <app-title
      class="app-title"
      :title="APP_TITLE"
    />
    <app-content class="app-content" />
  </div>
</template>

<script setup>
import AppTitle from './components/AppTitle.vue';
import AppContent from './components/AppContent.vue';
import { ref } from '@vue/reactivity';
const APP_TITLE = 'My Todo List Application';
</script>
<style>
.container {
  width: 900px;
  margin: 0 auto;
  border: 1px solid #ccc;
  padding: 10px;
  padding-bottom: 10px;
}

.app-title {
  text-align: center;
}

.app-content {
  border: 1px solid #ccc;
  padding: 10px;
}
</style>
