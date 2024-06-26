<template>
  <div class="container">
    <div>
      <select size="2" v-model="selectedOption">
        <option value="1">button 1</option>
        <option value="2">button 2</option>
      </select>
    </div>

    <div v-if="selectedOption === '1'" class="template">
      <button class="slds-button">Button</button>
    </div>

    <div v-if="selectedOption === '2'" class="template">
      <button class="slds-button slds-button_neutral">Button</button>
    </div>
  </div>
</template>

<script setup>
const selectedOption = ref("1");
</script>

<style>
.container {
  display: flex;
  gap: 20px;
  padding: 20px;
}
</style>
