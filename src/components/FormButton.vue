<template>
  <div class="form-button">
    <button
        v-if="!!props.todoSelected"
        @click="updateHandler"
    >Update</button>

    <button
        v-else
        @click="storeHandler"
    >Create New</button>
  </div>
</template>

<script setup>
import { defineEmits, defineProps } from 'vue';

const emit = defineEmits(['onStore', 'onUpdate']);
const props = defineProps({
    todoSelected: {
        type: Object,
        default: null,
    }
});

const storeHandler = () => {
    emit('onStore');
}

const updateHandler = () => {
    emit('onUpdate');
}
</script>
