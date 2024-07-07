<template>
  <section role="dialog" tabindex="-1" aria-modal="true" aria-labelledby="header43" class="slds-fade-in-open slds-modal_large slds-app-launcher">
    <div class="slds-modal__container">
      <div class="slds-modal__header slds-grid slds-grid_align-spread slds-grid_vertical-align-center">
        <h2 id="header43" class="slds-text-heading_medium"><slot></slot></h2>
      </div>
      <div class="slds-modal__content slds-app-launcher__content slds-p-around_medium" id="modal-content-id-1">
        <div class="slds-section slds-is-open">
          <div class="slds-section__content" id="appsContent">
            <div class="slds-assistive-text" id="drag-live-region" aria-live="assertive"></div>
            <ul class="slds-grid slds-grid_pull-padded slds-wrap">
              <li v-for="item in items" :key="item.label" class="slds-p-horizontal_small slds-size_1-of-1 slds-medium-size_1-of-3">
                <div draggable="true" class="slds-app-launcher__tile slds-text-link_reset slds-is-draggable">
                  <div class="slds-app-launcher__tile-figure">
                    <span class="slds-avatar slds-avatar_large">
                      <abbr class="slds-avatar__initials slds-icon-custom-27" :style="{ backgroundColor: item.color }" :title="item.label">{{
                        abbreviateLabel(item.label)
                      }}</abbr>
                    </span>
                  </div>
                  <div class="slds-app-launcher__tile-body">
                    <a v-if="item.link" :href="item.link">{{ item.label }}</a>
                    <div v-else-if="item.onClick" @click="item.onClick">{{ item.label }}</div>
                    <div v-else>Error</div>
                    <p>{{ item.description }}</p>
                    <div
                      class="slds-popover slds-popover_tooltip slds-nubbin_top-right slds-hide"
                      role="tooltip"
                      id="help-0"
                      style="position: absolute; top: 80px; right: 30px"
                    >
                      <div class="slds-popover__body"></div>
                    </div>
                  </div>
                </div>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
defineProps({
  items: Array,
});

const abbreviateLabel = (label) => {
  const words = label.split(" ");
  if (words.length > 1) {
    return words.map((word) => word[0].toUpperCase()).join("");
  } else {
    return label.slice(0, 2).toUpperCase();
  }
};
</script>

<style>
.slds-modal_large {
  max-width: 1000px;
}

.slds-app-launcher__content {
  flex: initial !important;
}

.slds-modal__close {
  margin-left: auto;
  position: relative !important;
  bottom: 0.5rem;
  top: initial !important;
}
</style>
