<script setup>
import NotesSection from './NotesSection.vue'

const allData = [
  {
    title: 'DO NOW',
    notesList: [
      {
        key: '',
        text: 'Sign documents',
        dateDisplay: 'Dec 11, 2021 Tues'
      },
      {
        key: '',
        text: 'Create figma designs',
        dateDisplay: 'Dec 12, 2021 Tues'
      }
    ]
  },
  {
    title: 'SCHEDULE',
    notesList: [
      {
        key: '',
        text: 'Sign documents',
        dateDisplay: 'Dec 11, 2021 Tues'
      },
      {
        key: '',
        text: 'Create figma designs',
        dateDisplay: 'Dec 12, 2021 Tues'
      }
    ]
  },
  {
    title: 'DELEGATE',
    notesList: [
      {
        key: '',
        text: 'Sign documents',
        dateDisplay: 'Dec 11, 2021 Tues'
      },
      {
        key: '',
        text: 'Create figma designs',
        dateDisplay: 'Dec 12, 2021 Tues'
      }
    ]
  },
  {
    title: 'DELETE',
    notesList: [
      {
        key: '',
        text: 'Sign documents',
        dateDisplay: 'Dec 11, 2021 Tues'
      },
      {
        key: '',
        text: 'Create figma designs',
        dateDisplay: 'Dec 12, 2021 Tues'
      }
    ]
  }
]
</script>

<template>
  <div class="row home-page">
    <div class="page-section sidebar">
      <div class="sidebar-inner-section">
        <div class="list-section">
          <span class="Note-Text backlog">write script</span>
          <span class="Note-Text backlog">research on vue.js</span>
          <span class="Note-Text backlog">study django</span>
          <span class="Note-Text backlog">write script</span>
          <span class="Note-Text backlog">research on vue.js</span>
          <span class="Note-Text backlog">study django</span>
        </div>
        <div class="Button">ADD BACKLOG</div>
      </div>
    </div>
    <div class="page-section main-area grid-section">
      <NotesSection
        v-for="(notesSection, index) in allData"
        :key="notesSection.title"
        :notes-section="notesSection"
        :box-class="`box${index + 1}`"
      ></NotesSection>
    </div>
  </div>
  <img alt="Vue logo" class="trash-icon" src="@/assets/trash-icon.png" width="125" height="125" />
  <div class="icon-bar">
    <a class="active" href="#"><i class="fa fa-home"></i></a>
    <a href="#"><i class="fa fa-search"></i></a>
    <a href="#"><i class="fa fa-envelope"></i></a>
    <a href="#"><i class="fa fa-globe"></i></a>
    <a href="#"><i class="fa fa-trash"></i></a>
  </div>
</template>

<style scoped lang="scss">
.home-page {
  background-color: var(--base-white);
  width: 95%;

  /* Clear floats after the columns */
  :after {
    content: '';
    display: table;
    clear: both;
  }
}

.sidebar {
  float: left;
  width: 33.33%;
  height: 100vh;
  display: flex;
  align-items: stretch;

  .sidebar-inner-section {
    width: 100%;
    display: flex;
    flex-direction: column;
    margin: 20px;
    background-color: var(--base-light-pink);

    .list-section {
      margin: 20px;
      display: flex;
      flex-direction: row;
      gap: 10px;
      flex-wrap: wrap;

      .backlog {
        color: var(--base-gray);
        padding: 10px;
        height: 40px;
        background-color: var(--base-white);
        display: flex;
        justify-content: center;
        align-items: center;
      }
    }
  }
}

.main-area {
  float: left;
  width: 66.67%;
  height: 100vh;
}

.grid-section {
  display: flex;
  flex-flow: row wrap;
}

.trash-icon {
  position: fixed;
  bottom: 10px;
  right: 10px;
}

.icon-bar {
  width: 90px;
  background-color: #555;
  position: absolute;
  top: 10px;
  right: 10px;

  a {
    display: block;
    text-align: center;
    padding: 16px;
    transition: all 0.3s ease;
    color: white;
    font-size: 36px;
  }

  a:hover {
    background-color: #000;
  }

  .active {
    background-color: #04aa6d;
  }
}

/* Responsive layout - when the screen is less than 600px wide */
@media screen and (max-width: 600px) {
  .home-page {
    width: 100%;
  }

  .page-section {
    width: 100%;
  }

  .grid-section {
    .box {
      flex-basis: 100%;
      border: var(--base-white);
    }
  }
}
</style>
