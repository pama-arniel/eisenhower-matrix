<script setup>
const MIN_DISPLAYED_LENGTH = 5

defineProps({
  notesSection: {
    type: Object,
    required: true
  },
  boxClass: {
    type: String,
    required: true
  }
})
</script>

<template>
  <div :class="`box ${boxClass}`">
    <h1 class="Title-Text">{{ notesSection.title }}</h1>
    <div v-for="note in notesSection.notesList" :key="note.key" class="rectangle-note">
      <span class="Note-Text">{{ note.text }}</span>
      <span class="Note-Subtext">• {{ note.dateDisplay }}</span>
    </div>
    <div
      v-for="filler in MIN_DISPLAYED_LENGTH - notesSection.notesList.length"
      :key="filler"
      class="rectangle-note note-filler"
    ></div>
  </div>
</template>

<style scoped lang="scss">
.box {
  flex-basis: 50%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: stretch;
  flex-wrap: wrap;
  gap: 10px;
  height: 50%;
}

.box1 {
  border-right: solid 4px var(--base-dark-pink);
  border-bottom: solid 4px var(--base-dark-pink);
}

.box2 {
  border-bottom: solid 4px var(--base-dark-pink);
}

.box3 {
  border-right: solid 4px var(--base-dark-pink);
}

.rectangle-note {
  height: 60px;
  background-color: var(--base-white);
  filter: drop-shadow(0px 2px 2px rgba(0, 0, 0, 0.25));
  width: 95%;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
