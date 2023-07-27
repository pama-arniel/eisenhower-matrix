<script setup>
import NotesSection from './NotesSection.vue'
import { ref } from 'vue'

const showModal = ref(false)
const noteTitle = ref('')
const currentChosenStatus = ref('')
const chosenDate = ref()

const chooseStatus = (chosenStatusName) => {
  if (currentChosenStatus.value == '' || currentChosenStatus.value != chosenStatusName) {
    currentChosenStatus.value = chosenStatusName
  } else {
    currentChosenStatus.value = ''
  }
}

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
        <div
          class="Button"
          @click="
            () => {
              console.log('show modal')
              showModal = !showModal
            }
          "
        >
          ADD BACKLOG
        </div>
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
  <div class="add-backlog-modal" v-if="showModal">
    <div class="section-to-be-edited">
      <img
        alt="close icon"
        class="close-icon"
        src="@/assets/x-icon.png"
        width="28"
        height="28"
        @click="
          () => {
            showModal = false
          }
        "
      />
      <div class="modal-fields">
        <div class="upper-section">
          <input
            v-model="noteTitle"
            class="note-title Edit-Note-Title"
            placeholder="Add title"
            type="text"
          />
          <div class="status-section">
            <div
              class="note-status Edit-Note-Status"
              :class="{ chosen: currentChosenStatus == 'Do now' }"
              @click="chooseStatus('Do now')"
            >
              Do now
            </div>
            <div
              class="note-status Edit-Note-Status"
              :class="{ chosen: currentChosenStatus == 'Schedule' }"
              @click="chooseStatus('Schedule')"
            >
              Schedule
            </div>
            <div
              class="note-status Edit-Note-Status"
              :class="{ chosen: currentChosenStatus == 'Delegate' }"
              @click="chooseStatus('Delegate')"
            >
              Delegate
            </div>
            <div
              class="note-status Edit-Note-Status"
              :class="{ chosen: currentChosenStatus == 'Delete' }"
              @click="chooseStatus('Delete')"
            >
              Delete
            </div>
            <div
              class="note-status Edit-Note-Status"
              :class="{ chosen: currentChosenStatus == 'Backlog' }"
              @click="chooseStatus('Backlog')"
            >
              Backlog
            </div>
          </div>
        </div>
        <div class="time-and-date-picker">
          <img
            alt="clock icon"
            class="clock-icon"
            src="@/assets/clock-icon.png"
            width="36"
            height="38"
          />
          <VueDatePicker v-model="chosenDate"></VueDatePicker>
        </div>
        <div class="note-description">
          <img
            alt="detail icon"
            class="detail-icon"
            src="@/assets/detail-icon.png"
            width="42"
            height="43"
          />
          <textarea
            class="note-description-text Edit-Note-Description"
            placeholder="Add description"
          ></textarea>
        </div>
        <div class="save-section">
          <div
            class="Button"
            style="width: 120px"
            @click="
              () => {
                console.log('show modal')
                showModal = !showModal
              }
            "
          >
            Save
          </div>
        </div>
      </div>
    </div>
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

    .Button {
      margin: auto 10px 10px 10px;
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

.add-backlog-modal {
  background: var(--base-modal-background);
  height: 100%;
  width: 100%;
  position: absolute;
  z-index: 1000;

  .section-to-be-edited {
    width: 800px;
    background: var(--base-white);
    box-shadow: 0px 4px 4px 0px rgba(0, 0, 0, 0.25);
    position: absolute;
    bottom: 20px;
    left: 20px;

    .close-icon {
      width: 28px;
      height: 28px;
      position: absolute;
      top: 20px;
      right: 20px;
      cursor: pointer;
    }

    .modal-fields {
      margin: 60px 20px 20px 20px;
      display: flex;
      flex-direction: column;
      gap: 40px;
      height: 100%;

      .upper-section {
        margin-left: 60px;

        input.note-title {
          width: 100%;
          padding: 15px 20px;
          margin: 8px 0;
          border: none;
          border-bottom: 0.5px solid var(--base-dark-pink);
          -webkit-transition: 0.2s;
        }

        input.note-title:focus {
          outline: none !important;
          border: 3px solid var(--base-light-pink);
        }

        .status-section {
          display: flex;
          flex-direction: row;
          gap: 10px;

          .note-status {
            cursor: pointer;
            border-radius: 10px;
            padding: 10px 20px;
          }

          .chosen {
            color: var(--base-dark-pink);
            background: var(--base-transparent-pink);
          }
        }
      }

      .time-and-date-picker {
        display: flex;
        flex-direction: row;
        gap: 14px;

        .clock-icon {
          width: 36px;
          height: 38px;
          margin-left: 6px;
        }
      }

      .note-description {
        display: flex;
        flex-direction: row;
        gap: 14px;
        height: 128px;

        .detail-icon {
          width: 42px;
          height: 43px;
        }

        .note-description-text {
          border: none;
          resize: none;
          width: 100%;
          background-color: var(--base-text-area-background);
          padding: 10px;
        }

        .note-description-text:focus {
          outline: none !important;
          border: 3px solid var(--base-light-pink);
        }
      }

      .save-section {
        display: flex;
        justify-content: flex-end;
      }
    }
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
