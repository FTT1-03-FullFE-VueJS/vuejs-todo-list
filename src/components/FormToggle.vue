<template>
  <div class="form-toggle">
    <button
        type="button"
        @click="toggleForm"
    >
        <span>{{ props.isShowForm ? 'Hidden Form' : 'Show Form' }}</span>
    </button>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

const emit = defineEmits(['onToggle']);
const props = defineProps({
    isShowForm: {
        type: Boolean,
        default: false,
    },
})

const toggleForm = () => {
    emit('onToggle');
}
</script>
