<template>
  <div class="content-control">
    <control-search
        :search-input="searchInput"
        @on-search="changeSearchInput"
    />
    <control-sort />
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';
import ControlSearch from './ControlSearch.vue';
import ControlSort from './ControlSort.vue';
const emit = defineEmits(['onSearch']);
const props = defineProps({
    searchInput: {
        type: String,
        default: '',
    }
});

const changeSearchInput = (value) => {
    emit('onSearch', value);
}
</script>
<style>
.content-control {
  display: flex;
}
</style>
