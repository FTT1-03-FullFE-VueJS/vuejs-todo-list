<template>
  <div class="content-form">
    <div class="content-form__top">
      <form-toggle
        :is-show-form="props.isShowForm"
        @on-toggle="toggleForm"
      />
    </div>
    <div class="content-form__bottom">
      <template v-if="props.isShowForm">
        <form-input
            :todo-input="todoInput"
            @on-input="inputChangeHandler"
        />
        <form-button
            :todo-selected="props.todoSelected"
            @on-store="storeHandler"
            @on-update="updateHandler"
        />
      </template>
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';
import FormInput from './FormInput.vue';
import FormButton from './FormButton.vue';
import FormToggle from './FormToggle.vue';

const emit = defineEmits(['onToggle', 'onInput', 'onStore', 'onUpdate']);
const props = defineProps({
    // Props of this component
    isShowForm: {
        type: Boolean,
        default: false,
    },
    todoInput: {
        type: String,
        default: ''
    },
    todoSelected: {
        type: Object,
        default: null,
    }
});

const toggleForm = () => {
    emit('onToggle');
}

const inputChangeHandler = (value) => {
    emit('onInput', value);
}

const storeHandler = () => {
    emit('onStore');
}

const updateHandler = () => {
    emit('onUpdate');
}
</script>
<style>
.content-form__top {
  margin-bottom: 5px;
}
.content-form__bottom {
  display: flex;
}
</style>
