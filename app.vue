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
        <option value="16">Timeline</option>
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

      <story-timeline
        v-if="selectedOption === '16'"
        :items="timelineItems"
        :style="{ backgroundColor: '#fff', padding: '20px', borderRadius: '5px' }"
      ></story-timeline>
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

const timelineItems = ref([
  {
    type: "task",
    title: "Review proposals for EBC deck with larger team and have marketing review this week",
    description: "You created a task with Charlie Gomez",
    time: "9:00am | 3/20/17",
    user: "Charlie Gomez",
    detailedDescription: "Need to finalize proposals and brand details before the meeting",
    relatedTo: "Tesla Cloudhub + Anypoint Connectors",
    link: "https://example.com",
  },
  {
    type: "log_a_call",
    title: "Mobile conversation on Monday",
    description: "You logged a call with Adam Chan",
    time: "10:00am | 3/23/17",
    user: "Adam Chan",
    detailedDescription: "Adam seemed interested in closing this deal quickly! Let’s move.",
    relatedTo: "Tesla Cloudhub + Anypoint Connectors",
    link: "https://example.com",
  },
  {
    type: "email",
    title: "Mobile conversation on Monday with the new global team",
    description: "You sent an email to Lea Chan",
    time: "10:00am | 3/24/17",
    user: "Lea Chan",
    detailedDescription:
      "Hi everyone, Thanks for meeting with the team today and going through the proposals we saw. This goes on and wraps if needed.",
    relatedTo: "Lea Chan",
    link: "https://example.com",
  },
  {
    type: "event",
    title: "EBC Follow up call",
    description: "You created an event with Aida Lee",
    time: "10:30am | 3/24/17",
    user: "Aida Lee",
    detailedDescription: "Let's discuss the 2025 product roadmap and address any questions",
    relatedTo: "Jason Dewar (Organizer) + 5 others",
    link: "https://example.com",
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
