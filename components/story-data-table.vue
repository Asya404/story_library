<template>
  <table class="slds-table slds-table_cell-buffer slds-table_bordered" aria-labelledby="element-with-table-label other-element-with-table-label">
    <thead>
      <tr class="slds-line-height_reset">
        <th v-for="heading in cellKeys" :key="heading" class="" scope="col">
          <div class="slds-truncate" :title="heading">{{ heading }}</div>
        </th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(item, index) in items" :key="index" class="slds-hint-parent">
        <td v-for="(value, key) in item" :key="key" :data-label="key">
          <div class="slds-truncate" :title="value">{{ value }}</div>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script setup>
const props = defineProps({
  headings: Array,
  items: Array,
});

const cellKeys = props.headings ? props.headings : Object.keys(props.items[0]);
</script>
