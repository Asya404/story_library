<template>
  <div class="container">
    <div>
      <select size="10" v-model="selectedOption" @change="setToLS">
        <option value="1">Button</option>
        <option value="2">Neutral Button</option>
        <option value="3">Brand Button</option>
        <option value="4">Card</option>
        <option value="5">Collapsed Card</option>
        <option value="6">Loading Card</option>
        <option value="12">Carousel</option>
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

      <story-carousel v-if="selectedOption === '12'" :items="carouselItems"></story-carousel>
    </div>
  </div>
</template>

<script setup>
const selectedOption = ref("");

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

.wrapper {
  width: 100%;
  max-width: 400px;
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
