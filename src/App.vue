<script setup lang="ts">
 import { ref } from 'vue';
import BaseInput from '../lib/BaseInput.vue';
 const countVModel = ref(1);
 const invalidCntErr = ref("");

 const checkCount = () => {
 if (countVModel.value < 1) {
    invalidCntErr.value = "Can't less than 1"
  } else if (countVModel.value > 999) {
    invalidCntErr.value = "Can't greater than 999";
  } else invalidCntErr.value = "";
};
</script>

<template>
    <BaseInput
      v-model="countVModel"
      type="number"
      input-group-class="input-group-sm w-25 ms-2"
      :modifier-class="`${invalidCntErr ? 'is-invalid' : ''}`"
      :feedback="invalidCntErr"
      feedback-class="text-nowrap"
      @keyup="checkCount"
    />
</template>

