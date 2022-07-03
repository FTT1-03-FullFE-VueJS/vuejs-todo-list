<template>
  <div class="content-control">
    <control-search />
    <control-sort />
  </div>
</template>

<script setup>
import ControlSearch from './ControlSearch.vue';
import ControlSort from './ControlSort.vue';
</script>
<style>
.content-control {
  display: flex;
}
</style>