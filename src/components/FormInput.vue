<template>
  <div class="form-input">
    <input
        type="text"
        :value="props.todoInput"
        @input="inputChangeHandler"
    >
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

const emit = defineEmits(['onInput']);

const props = defineProps({
    todoInput: {
        type: String,
        default: ''
    },
});

const inputChangeHandler = (evt) => {
    const value = evt.target.value;
    emit('onInput', value);
};
</script>
