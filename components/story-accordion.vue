<template>
  <div class="slds-card">
    <ul class="slds-accordion">
      <li v-for="(item, index) in items" :key="item.label" class="slds-accordion__list-item" @click="toggleAccordion(index)">
        <section :class="['slds-accordion__section', { 'slds-is-open': opened[index] }]">
          <div class="slds-accordion__summary">
            <h2 class="slds-accordion__summary-heading">
              <button
                class="slds-button slds-button_reset slds-accordion__summary-action"
                aria-controls="referenceId-42"
                aria-expanded="true"
                title="Accordion summary"
              >
                <div class="accordion-icon slds-accordion__summary-action-icon slds-button__icon slds-button__icon_left">▼</div>
                <span class="slds-accordion__summary-content">{{ item.label }}</span>
              </button>
            </h2>
          </div>
          <div class="slds-accordion__content" id="referenceId-42">{{ item.content }}</div>
        </section>
      </li>
    </ul>
  </div>
</template>

<script setup>
const props = defineProps({
  items: Array,
});

const opened = ref(props.items.map(() => false));

const toggleAccordion = (index) => {
  opened.value = opened.value.map((state, i) => (i === index ? !state : false));
};
</script>

<style>
.accordion-icon {
  margin-right: 10px;
}
</style>
