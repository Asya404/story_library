<template>
  <div class="container">
    <div>
      <select size="3" v-model="selectedOption" @change="setToLS">
        <option value="1">Button</option>
        <option value="2">Neutral Button</option>
        <option value="3">Brand Button</option>
      </select>
    </div>

    <story-button v-if="selectedOption === '1'" base></story-button>
    <story-button v-if="selectedOption === '2'" neutral></story-button>
    <story-button v-if="selectedOption === '3'" brand></story-button>
  </div>
</template>

<script setup>
const selectedOption = ref("");

const setToLS = () => {
  localStorage.setItem("selectedOption", selectedOption.value);
};

onMounted(() => {
  selectedOption.value = localStorage.getItem("selectedOption") || "1";
});
</script>

<style>
.container {
  display: flex;
  align-items: flex-start;
  gap: 20px;
  padding: 20px;
}
</style>
