<template>
  <div class="slds-notify_container slds-is-relative">
    <div :class="toastClass" role="status">
      <span class="slds-assistive-text">info</span>
      <span class="slds-icon_container slds-icon-utility-info slds-m-right_small slds-no-flex slds-align-top" title="Description of icon when needed">
        <span v-if="props.success" class="slds-icon slds-icon_small" aria-hidden="true" :style="{ fontSize: '25px' }">✅</span>
        <span v-else-if="props.warning" class="slds-icon slds-icon_small" aria-hidden="true" :style="{ fontSize: '25px' }">❗</span>
        <span v-else-if="props.error" class="slds-icon slds-icon_small" aria-hidden="true" :style="{ fontSize: '25px' }">⛔</span>
        <span v-else class="slds-icon slds-icon_small" aria-hidden="true" :style="{ fontSize: '25px' }">🛈</span>
      </span>
      <div class="slds-notify__content">
        <h2 class="slds-text-heading_small"><slot></slot></h2>
      </div>
      <div class="slds-notify__close">
        <button class="slds-button slds-button_icon slds-button_icon-inverse" title="Close">
          <span class="slds-button__icon slds-button__icon_large" aria-hidden="true" :style="{ fontSize: '25px' }">⨯</span>
          <span class="slds-assistive-text">Close</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  success: Boolean,
  warning: Boolean,
  error: Boolean,
});

const toastClass = computed(() => ({
  "slds-notify": true,
  "slds-notify_toast": true,
  "slds-theme_info": !props.success,
  "slds-theme_success": props.success,
  "slds-theme_warning": props.warning,
  "slds-theme_error": props.error,
}));
</script>
