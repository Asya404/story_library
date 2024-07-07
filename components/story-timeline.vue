<template>
  <ul class="slds-timeline">
    <li v-for="(item, index) in items" :key="index">
      <div class="slds-timeline__item_expandable slds-timeline__item_task">
        <div class="slds-media">
          <div class="slds-media__figure">
            <button class="slds-button slds-button_icon" aria-controls="task-item-base-65">
              <span class="slds-button__icon slds-timeline__details-action-icon" aria-hidden="true">⮞</span>
            </button>
            <div class="slds-icon_container slds-icon-standard-task slds-timeline__icon" title="task">
              <span aria-hidden="true">📝</span>
            </div>
          </div>
          <div class="slds-media__body">
            <div class="slds-grid slds-grid_align-spread slds-timeline__trigger">
              <div class="slds-grid slds-grid_vertical-align-center slds-truncate_container_75 slds-no-space">
                <h3 class="slds-truncate" title="Review proposals for EBC deck with larger team and have marketing review this">
                  <a :href="item.link">
                    <strong>{{ item.title }}</strong>
                  </a>
                </h3>
                <div class="slds-no-flex"></div>
              </div>
              <div class="slds-timeline__actions slds-timeline__actions_inline">
                <p class="slds-timeline__date">{{ item.time }}</p>
              </div>
            </div>
            <p class="slds-m-horizontal_xx-small">
              {{ item.description }}
            </p>
          </div>
        </div>
      </div>
    </li>
  </ul>
</template>

<script setup>
defineProps({
  items: Array,
});
</script>

<style scoped>
.slds-icon {
  display: inline-block;
}

.slds-icon_container {
  line-height: inherit;
  border: 1px solid #fff;
}

.slds-timeline__item_expandable .slds-media__figure .slds-button_icon {
  margin-right: 0.9rem;
}
</style>
