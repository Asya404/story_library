<template>
  <div class="container">
    <div>
      <select size="20" v-model="selectedOption" @change="setToLS">
        <option value="1">Button</option>
        <option value="2">Neutral Button</option>
        <option value="3">Brand Button</option>
        <option value="4">Card</option>
        <option value="5">Collapsed Card</option>
        <option value="6">Loading Card</option>
        <option value="7">Accordion</option>
        <option value="8">Toast</option>
        <option value="9">Success Toast</option>
        <option value="10">Warning Toast</option>
        <option value="11">Error Toast</option>
        <option value="12">Carousel</option>
        <option value="15">App Launcher</option>
      </select>
    </div>
    <div class="wrapper">
      <story-button v-if="selectedOption === '1'" base></story-button>
      <story-button v-if="selectedOption === '2'" neutral></story-button>
      <story-button v-if="selectedOption === '3'" brand></story-button>

      <story-card v-if="selectedOption === '4'" imgLink="https://img.icons8.com/?size=100&id=86128&format=png&color=7950F2">
        <template v-slot:header>Accounts</template>
        <template v-slot:body>Anything can go into the card body</template>
      </story-card>

      <story-card v-if="selectedOption === '5'" collapsed imgLink="https://img.icons8.com/?size=100&id=86128&format=png&color=7950F2">
        <template v-slot:header>Accounts</template>
      </story-card>

      <story-card v-if="selectedOption === '6'" loading imgLink="https://img.icons8.com/?size=100&id=86128&format=png&color=7950F2">
        <template v-slot:header>Accounts</template>
      </story-card>

      <story-accordion v-if="selectedOption === '7'" :items="accordionItems"></story-accordion>

      <story-toast v-if="selectedOption === '8'">26 potential duplicate leads were found.</story-toast>
      <story-toast v-if="selectedOption === '9'" success>Account ACME - 100 widgets was created.</story-toast>
      <story-toast v-if="selectedOption === '10'" warning>Can’t share file “report-q3.pdf” with the selected users.</story-toast>
      <story-toast v-if="selectedOption === '11'" error>Can’t save lead “Sally Wong” because another lead has the same name.</story-toast>

      <story-carousel v-if="selectedOption === '12'" :items="carouselItems"></story-carousel>

      <story-app-launcher v-if="selectedOption === '15'" :items="appLauncherItems">App launcher</story-app-launcher>
    </div>
  </div>
</template>

<script setup>
const selectedOption = ref("");

const accordionItems = ref([
  {
    label: "Accordion summary a",
    content: "Accordion details - A",
  },
  {
    label: "Accordion summary b",
    content: "Accordion details - B",
  },
  {
    label: "Accordion summary c",
    content: "Accordion details - C",
  },
]);

const carouselItems = ref([
  {
    label: "Item 1",
    description: "Item 1 description",
    imgLink: "https://images.pexels.com/photos/6289026/pexels-photo-6289026.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
  },
  {
    label: "Item 2",
    description: "Item 2 description",
    imgLink: "https://images.pexels.com/photos/6289026/pexels-photo-6289026.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
  },
  {
    label: "Item 3",
    description: "Item 3 description",
    imgLink: "https://images.pexels.com/photos/6289026/pexels-photo-6289026.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
  },
]);

const appLauncherItems = ref([
  {
    label: "Sales Cloud",
    description: "The primary internal Salesforce org",
    link: "https://www.google.com",
    color: "#e3d067",
  },
  {
    label: "Marketing Cloud",
    description: "Salesforce Marketing Cloud lets businesses of any size",
    link: "https://www.google.com",
    color: "#6488e3",
  },
  {
    label: "HR Concierge",
    description: "Community for managing employee benefits",
    link: "https://www.google.com",
    color: "#e36868",
  },
  {
    label: "My Money",
    description: "Manage your finances across multiple financial platforms",
    link: "https://www.google.com",
    color: "#54c473",
  },
  {
    label: "Call Center",
    description: "The key to call center and contact center management",
    link: "https://www.google.com",
    color: "#bf7b66",
  },
  {
    label: "Customer Support",
    description: "Areas of Focus are used to track customer support",
    link: "https://www.google.com",
    color: "#49bcd3",
  },
]);

const setToLS = () => {
  localStorage.setItem("selectedOption", selectedOption.value);
};

onMounted(() => {
  selectedOption.value = localStorage.getItem("selectedOption") || "1";
});
</script>

<style>
.container {
  display: flex;
  align-items: center;
  gap: 50px;
}

.slds-card {
  min-width: 400px;
}

select {
  border: none;
  font-size: 14px;
}

select:focus {
  outline: none;
}

select option {
  padding: 7px 30px 7px 20px;
}
</style>
