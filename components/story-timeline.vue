<template>
  <ul class="slds-timeline">
    <li v-for="(item, index) in items" :key="index">
      <div class="slds-timeline__item_expandable slds-timeline__item_task" :class="{ 'slds-is-open': expanded[index] }">
        <div class="slds-media">
          <div class="slds-media__figure">
            <button
              class="slds-button slds-button_icon"
              :class="{ 'slds-icon-expanded': expanded[index] }"
              @click="toggleItem(index)"
              :aria-controls="'task-item-expanded-' + index"
              :aria-expanded="expanded[index]"
            >
              <span class="slds-button__icon slds-timeline__details-action-icon" aria-hidden="true">⮞</span>
            </button>
            <div
              class="slds-icon_container slds-icon-standard-task slds-timeline__icon"
              :class="{
                'slds-icon-standard-log-a-call': item.type === 'log_a_call',
                'slds-icon-standard-email': item.type === 'email',
                'slds-icon-standard-event': item.type === 'event',
              }"
              title="task"
            >
              <span aria-hidden="true">📝</span>
            </div>
          </div>
          <div class="slds-media__body">
            <div class="slds-grid slds-grid_align-spread slds-timeline__trigger">
              <div class="slds-grid slds-grid_vertical-align-center slds-truncate_container_75 slds-no-space">
                <h3 class="slds-truncate" :title="item.title">
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
            <article
              v-if="expanded[index]"
              class="slds-box slds-timeline__item_details slds-theme_shade slds-m-top_x-small slds-m-horizontal_xx-small slds-p-around_medium"
              :id="'task-item-expanded-' + index"
            >
              <ul class="slds-list_horizontal slds-wrap">
                <li class="slds-grid slds-grid_vertical slds-size_1-of-2 slds-p-bottom_small">
                  <span class="slds-text-title slds-p-bottom_x-small">Name</span>
                  <span class="slds-text-body_medium slds-truncate" :title="item.user">
                    <a href="#">{{ item.user }}</a>
                  </span>
                </li>
                <li class="slds-grid slds-grid_vertical slds-size_1-of-2 slds-p-bottom_small">
                  <span class="slds-text-title slds-p-bottom_x-small">Related To</span>
                  <span class="slds-text-body_medium slds-truncate" :title="item.relatedTo">
                    <a href="#">{{ item.relatedTo }}</a>
                  </span>
                </li>
              </ul>
              <div>
                <span class="slds-text-title">Description</span>
                <p class="slds-p-top_x-small">{{ item.detailedDescription }}</p>
              </div>
            </article>
          </div>
        </div>
      </div>
    </li>
  </ul>
</template>

<script setup>
const props = defineProps({
  items: Array,
});

const expanded = ref(props.items.map(() => false));

function toggleItem(index) {
  expanded.value = expanded.value.map((state, i) => (i === index ? !state : false));
}
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

.slds-icon-expanded {
  transform: rotate(90deg);
}
</style>
