<template>
  <button :class="buttonClass">Button</button>
</template>

<script setup>
const props = defineProps({
  base: Boolean,
  neutral: Boolean,
  brand: Boolean,
});

const buttonClass = computed(() => ({
  "slds-button": true,
  "slds-button_neutral": props.neutral,
  "slds-button_brand": props.brand,
}));
</script>
