<template>
  <div class="app-content__wrapper">
    <div class="app-content__top">
      <content-control />
      <content-form />
    </div>
    <div class="app-content__bottom">
      <content-todos />
    </div>
  </div>
</template>

<script setup>
import ContentControl from './ContentControl.vue';
import ContentForm from './ContentForm.vue';
import ContentTodos from './ContentTodos.vue';
</script>
<style>
.app-content__top {
  display: flex;
  justify-content: space-between;
  margin-bottom: 10px;
  border-bottom: 1px solid #ccc;
  padding-bottom: 10px;
  align-items: center;
}
</style>