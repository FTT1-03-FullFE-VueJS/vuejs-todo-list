<template>
  <div class="control-sort">
    <div class="control-sort__type">
      <select name="" id="">
        <option value="">Title</option>
      </select>
    </div>
    <div class="control-sort__order">
      <select name="" id="" @change="sortOrderChange">
        <option value="asc">ASC</option>
        <option value="desc">DESC</option>
      </select>
    </div>
  </div>
</template>

<script setup>
import { ref, defineProps, defineEmits } from 'vue';
const sortOrder = ref('asc');

const emit = defineEmits(['onSort']);
const props = defineProps({
    sortOrder: {
        type: String,
        default: '',
    }
});

const sortOrderChange = (evt) => {
    const value = evt.target.value;
    emit('onSort', value);
}
</script>
<style>
.control-sort {
  display: flex;
}
</style>