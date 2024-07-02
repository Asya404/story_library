<template>
  <div class="slds-context-bar">
    <div class="slds-context-bar__primary">
      <div class="slds-context-bar__item slds-context-bar__dropdown-trigger slds-dropdown-trigger slds-dropdown-trigger_click slds-no-hover">
        <div class="slds-context-bar__icon-action">
          <button class="slds-button slds-icon-waffle_container slds-context-bar__button" title="Description of the icon when needed">
            <span class="slds-icon-waffle">
              <span class="slds-r1"></span>
              <span class="slds-r2"></span>
              <span class="slds-r3"></span>
              <span class="slds-r4"></span>
              <span class="slds-r5"></span>
              <span class="slds-r6"></span>
              <span class="slds-r7"></span>
              <span class="slds-r8"></span>
              <span class="slds-r9"></span>
            </span>
            <span class="slds-assistive-text">Open App Launcher</span>
          </button>
        </div>
        <span class="slds-context-bar__label-action slds-context-bar__app-name">
          <span class="slds-truncate" title="App Name"><slot></slot></span>
        </span>
      </div>
    </div>
    <nav class="slds-context-bar__secondary" role="navigation">
      <ul class="slds-grid">
        <li class="slds-context-bar__item" :class="{ 'slds-is-active': homeActive }" @click="setHomeActive">
          <a href="#" class="slds-context-bar__label-action" title="Home">
            <span class="slds-assistive-text">Current Page:</span>
            <span class="slds-truncate" title="Home">Home</span>
          </a>
        </li>
        <li
          v-for="item in items"
          :key="item.label"
          @click="toggleDropdown(item)"
          class="slds-context-bar__item slds-context-bar__dropdown-trigger slds-dropdown-trigger slds-dropdown-trigger_click"
          :class="{ 'slds-is-open': item.isOpen, 'slds-is-active': item.isOpen }"
        >
          <a href="#" class="slds-context-bar__label-action" title="Menu Item">
            <span class="slds-truncate" title="Menu Item">{{ item.label }}</span>
          </a>
          <div class="slds-context-bar__icon-action" :class="{ 'icon-up': item.isOpen, 'icon-down': !item.isOpen }">
            <button
              class="slds-button slds-button_icon slds-button_icon slds-context-bar__button"
              aria-haspopup="true"
              title="Open menu item submenu"
            >
              🔽
            </button>
          </div>
          <div class="slds-dropdown slds-dropdown_right">
            <ul class="slds-dropdown__list" role="menu">
              <li v-for="subItem in item.submenu" :key="subItem.label" class="slds-dropdown__item" role="presentation">
                <a :href="subItem.link" role="menuitem" tabindex="-1">
                  <span class="slds-truncate" title="Menu Item One">{{ subItem.label }}</span>
                </a>
              </li>
            </ul>
          </div>
        </li>
      </ul>
    </nav>
  </div>
</template>
<script setup>
const props = defineProps({
  items: Array,
});
let homeActive = ref(true);
props.items = ref(props.items.map((item) => ({ ...item, isOpen: false })));
const toggleDropdown = (toggledItem) => {
  toggledItem.isOpen = !toggledItem.isOpen;
  props.items.forEach((item) => {
    if (item !== toggledItem) {
      item.isOpen = false;
    }
  });
  toggledItem.isOpen && (homeActive = false);
};
const setHomeActive = () => {
  homeActive = true;
};
</script>
<style>
.icon-up {
  display: inline-block;
  transform: rotate(180deg);
}
.slds-button:focus {
  -webkit-box-shadow: none !important;
  box-shadow: none !important;
}
</style>