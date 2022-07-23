<template>
  <div class="control-search">
    <input type="text" :value="props.searchInput" @input="changeSearchInput">
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';
const emit = defineEmits(['onSearch']);
const props = defineProps({
    searchInput: {
        type: String,
        default: '',
    }
});

const changeSearchInput = (e) => {
    const value = e.target.value;
    emit('onSearch', value);
}

</script>
<style>
.control-search {
  margin-right: 10px;
}
</style>