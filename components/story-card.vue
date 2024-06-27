<template>
  <article class="slds-card">
    <div class="slds-card__header slds-grid">
      <header class="slds-media slds-media_center slds-has-flexi-truncate">
        <div class="slds-media__figure">
          <span class="slds-icon_container slds-icon-standard-account" title="account">
            <img class="slds-icon slds-icon_small" aria-hidden="true" width="15" height="15" :src="imgLink" alt="accounting" />
            <span class="slds-assistive-text">account</span>
          </span>
        </div>
        <div class="slds-media__body">
          <h2 class="slds-card__header-title">
            <a href="#" class="slds-card__header-link slds-truncate" title="Accounts">
              <span>
                <slot name="header"></slot>
              </span>
            </a>
          </h2>
        </div>
        <div v-if="!loading" class="slds-no-flex">
          <button class="slds-button slds-button_neutral">New</button>
        </div>
      </header>
    </div>

    <div class="slds-card__body slds-card__body_inner">
      <slot v-if="!collapsed" name="body"></slot>

      <div v-if="loading" role="status" class="slds-spinner slds-spinner_small">
        <span class="slds-assistive-text">Loading</span>
        <div class="slds-spinner__dot-a"></div>
        <div class="slds-spinner__dot-b"></div>
      </div>
    </div>
  </article>
</template>

<script setup>
const props = defineProps({
  imgLink: String,
  collapsed: Boolean,
  loading: Boolean,
});
</script>
