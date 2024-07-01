<template>
  <div class="slds-carousel">
    <div class="slds-carousel__stage">
      <div class="slds-carousel__panels" :style="{ transform: 'translateX(' + activePanelIndex * -100 + '%)' }">
        <div
          v-for="(item, index) in items"
          :key="item.label"
          class="slds-carousel__panel"
          :class="{ 'slds-is-active': activePanelIndex === index }"
          role="tabpanel"
          :aria-hidden="activePanelIndex !== index ? 'true' : null"
          :tabindex="activePanelIndex === index ? '0' : '-1'"
        >
          <a href="#" class="slds-carousel__panel-action slds-text-link_reset" @click="activatePanel(index)">
            <div class="slds-carousel__image">
              <img :src="item.imgLink" :alt="item.label" />
            </div>
            <div class="slds-carousel__content">
              <h2 class="slds-carousel__content-title">{{ item.label }}</h2>
              <p>{{ item.description }}</p>
            </div>
          </a>
        </div>
      </div>
      <ul class="slds-carousel__indicators" role="tablist">
        <li v-for="(item, index) in items" :key="index" class="slds-carousel__indicator" role="presentation">
          <a
            :id="'indicator-id-' + index"
            class="slds-carousel__indicator-action"
            :class="{ 'slds-is-active': activePanelIndex === index }"
            href="#"
            role="tab"
            :tabindex="activePanelIndex === index ? '0' : '-1'"
            :aria-selected="activePanelIndex === index ? 'true' : 'false'"
            @click="activatePanel(index)"
          >
            <span class="slds-assistive-text">{{ item.label }} tab</span>
          </a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
defineProps({
  items: Array,
});

const activePanelIndex = ref(0);

const activatePanel = (index) => {
  activePanelIndex.value = index;
};
</script>

<style>
.slds-carousel {
  max-width: 500px;
}
</style>
