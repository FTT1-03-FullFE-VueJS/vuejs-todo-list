<template>
  <div class="content-form">
    <div class="content-form__top">
      <form-toggle />
    </div>
    <div class="content-form__bottom">
      <form-input />
      <form-button />
    </div>
  </div>
</template>

<script setup>
import FormInput from './FormInput.vue';
import FormButton from './FormButton.vue';
import FormToggle from './FormToggle.vue';
</script>
<style>
.content-form__top {
  margin-bottom: 5px;
}
.content-form__bottom {
  display: flex;
}
</style>