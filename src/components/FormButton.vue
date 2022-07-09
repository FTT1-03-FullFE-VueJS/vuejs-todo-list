<template>
  <div class="form-button">
    <button
        @click="storeHandler"
    >Create new</button>
  </div>
</template>

<script setup>
import { defineEmits } from 'vue';

const emit = defineEmits(['onStore']);

const storeHandler = () => {
    emit('onStore');
}
</script>
