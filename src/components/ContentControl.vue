<template>
  <div class="content-control">
    <control-search
        :search-input="searchInput"
        @on-search="changeSearchInput"
    />
    <control-sort
        :sort-order="sortOrder"
        @on-sort="sortHandler"
    />
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';
import ControlSearch from './ControlSearch.vue';
import ControlSort from './ControlSort.vue';
const emit = defineEmits(['onSearch', 'onSort']);
const props = defineProps({
    searchInput: {
        type: String,
        default: '',
    },
    sortOrder: {
        type: String,
        default: '',
    }
});

const changeSearchInput = (value) => {
    emit('onSearch', value);
}
const sortHandler = (value) => {
    emit('onSort', value);
}
</script>
<style>
.content-control {
  display: flex;
}
</style>
