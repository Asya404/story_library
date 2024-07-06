<template>
  <div class="slds-form-element">
    <div class="slds-form-element__control">
      <div class="slds-combobox_container">
        <div class="slds-combobox slds-dropdown-trigger slds-dropdown-trigger_click" :class="{ 'slds-is-open': isOpen }">
          <div class="slds-combobox__form-element slds-input-has-icon slds-input-has-icon_right" role="none">
            <div
              role="combobox"
              tabindex="0"
              class="slds-input_faux slds-combobox__input slds-has-focus"
              aria-labelledby="combobox-label-id-134 combobox-id-2-selected-value"
              id="combobox-id-2-selected-value"
              aria-controls="listbox-id-4"
              aria-expanded="true"
              aria-haspopup="listbox"
              @click="toggleDropdown"
            >
              <span class="slds-truncate" id="combobox-value-id-107">{{ selectedLabel }}</span>
            </div>
            <span class="slds-icon_container slds-icon-utility-down slds-input__icon slds-input__icon_right" :class="{ active: isOpen }">
              <span class="slds-icon slds-icon slds-icon_x-small slds-icon-text-default" aria-hidden="true">▼</span>
            </span>
          </div>
          <div
            id="listbox-id-4"
            class="slds-dropdown slds-dropdown_length-5 slds-dropdown_fluid"
            role="listbox"
            aria-label="Dropdown Items"
            tabindex="0"
            aria-busy="false"
            v-show="isOpen"
          >
            <ul class="slds-listbox slds-listbox_vertical" role="presentation">
              <li v-for="option in options" :key="option.label" role="presentation" class="slds-listbox__item">
                <div @click="selectOption(option)" class="slds-media slds-listbox__option slds-listbox__option_plain slds-media_small" role="option">
                  <span class="slds-media__figure slds-listbox__option-icon"></span>
                  <span class="slds-media__body">
                    <span class="slds-truncate" title="Accounts">{{ option.label }}</span>
                  </span>
                </div>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  options: Array,
});

const isOpen = ref(false);
const selectedOption = ref(null);

const toggleDropdown = () => {
  isOpen.value = !isOpen.value;
};

const selectOption = (option) => {
  selectedOption.value = option;
  isOpen.value = false;
};

const selectedLabel = computed(() => {
  return selectedOption.value ? selectedOption.value.label : "Select an Option…";
});
</script>

<style scoped>
.slds-form-element {
  min-width: 500px;
}

.slds-combobox__input {
  padding: 5px;
  border-radius: 5px;
  background-color: #fff;
}

.slds-input__icon {
  color: #706e6b;
}

.slds-input__icon.active {
  transform: rotate(180deg);
}

.slds-select {
  display: none;
}
</style>
