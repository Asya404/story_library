<template>
  <div class="demo-only demo-only_viewport" style="height: 640px">
    <section role="dialog" tabindex="-1" aria-modal="true" aria-labelledby="id-of-modalheader-h1" class="slds-list-builder">
      <div class="slds-modal__container slds-modal__large">
        <div class="slds-modal__header">
          <h1 id="id-of-modalheader-h1" class="slds-text-heading_medium"><slot></slot></h1>
        </div>
        <div class="slds-modal__content slds-grid slds-grow" id="modal-content-id-1">
          <div class="slds-grid slds-grid_vertical">
            <div class="slds-scrollable slds-grow">
              <div class="slds-scrollable_none">
                <table
                  aria-multiselectable="true"
                  class="slds-table slds-no-row-hover slds-table_bordered slds-table_fixed-layout slds-table_resizable-cols"
                  role="grid"
                  aria-label="Example product list"
                >
                  <thead>
                    <tr class="slds-line-height_reset">
                      <th class="" scope="col" style="width: 3.75rem"></th>
                      <th v-for="(heading, index) in headings" :key="index" aria-sort="none" class="slds-is-resizable slds-is-sortable" scope="col">
                        <a class="slds-th__action slds-text-link_reset" href="#" role="button" tabindex="-1">
                          <span class="slds-assistive-text">Sort by: </span>
                          <div class="slds-grid slds-grid_vertical-align-center slds-has-flexi-truncate">
                            <span class="slds-truncate">{{ heading }}</span>
                          </div>
                        </a>
                        <div class="slds-resizable">
                          <input
                            type="range"
                            aria-label="Name column width"
                            class="slds-resizable__input slds-assistive-text"
                            id="cell-resize-handle-65"
                            max="1000"
                            min="20"
                            tabindex="-1"
                          />
                          <span class="slds-resizable__handle">
                            <span class="slds-resizable__divider"></span>
                          </span>
                        </div>
                      </th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr v-for="(item, index) in items" :key="index" aria-selected="false" class="slds-hint-parent">
                      <td class="slds-text-align_right" role="gridcell" tabindex="0">
                        <label class="slds-checkbox-button" for="example-unique-id-172">
                          <input type="checkbox" class="slds-assistive-text" id="example-unique-id-172" value="example-unique-id-172" tabindex="-1" />
                        </label>
                      </td>
                      <th scope="row">
                        <div class="slds-truncate" title="Analytics">{{ item.label }}</div>
                      </th>
                      <td role="gridcell">
                        <div class="slds-truncate" title="ANTLY">{{ item.productCode }}</div>
                      </td>
                      <td role="gridcell">
                        <div class="slds-truncate" title="5000.00">{{ item.listPrice }}</div>
                      </td>
                      <td role="gridcell">
                        <div class="slds-truncate" title="Analytics Product">{{ item.productFamily }}</div>
                      </td>
                    </tr>
                  </tbody>
                </table>
              </div>
            </div>
          </div>
        </div>
        <div class="slds-modal__footer">
          <button class="slds-button slds-button_neutral" aria-label="Cancel and close">Cancel</button>
          <button class="slds-button slds-button_brand">Next</button>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
defineProps({
  items: Array,
  headings: Array,
});
</script>

<style scoped>
.slds-modal__large {
  width: initial !important;
  max-width: 900px;
}
</style>
