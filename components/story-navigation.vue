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
          v-for="(item, index) in props.items"
          :key="item.label"
          @click="toggleDropdown(index)"
          class="slds-context-bar__item slds-context-bar__dropdown-trigger slds-dropdown-trigger slds-dropdown-trigger_click"
          :class="{ 'slds-is-open': opened[index], 'slds-is-active': opened[index] }"
        >
          <a href="#" class="slds-context-bar__label-action" title="Menu Item">
            <span class="slds-truncate" title="Menu Item">{{ item.label }}</span>
          </a>
          <div class="slds-context-bar__icon-action" :class="{ 'icon-up': opened[index], 'icon-down': !opened[index] }">
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

const opened = ref(props.items.map(() => false));

const toggleDropdown = (index) => {
  opened.value = opened.value.map((state, i) => (i === index ? !state : false));
  homeActive.value = false;
};

const setHomeActive = () => {
  homeActive.value = !opened.value.some((state) => state);
  homeActive.value = true;
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
