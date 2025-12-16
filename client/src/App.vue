<script>
import CustomInput from "./components/CustomInput.vue";

export default {
  components: { CustomInput },
  data() {
    return {
      tasks: [],
      newTask: "",
      notes: [],
      newNote: "",
      newNoteName: "",
      noteNames: [],
    };
  },
  methods: {
    addTask() {
      if (this.newTask == "") {
      } else {
        this.tasks.push(this.newTask);
        this.newTask = "";
      }
    },
    addNote() {
      if (this.newNote == "" || this.newNoteName == "") {
      } else {
        this.notes.push(this.newNote);
        this.newNote = "";
        this.noteNames.push(this.newNoteName);
        this.newNoteName = "";
      }
    },
    taskDone() {},
  },
};
</script>

<template>
  <div class="container">
    <div class="taskStack">
      <h1>To-do list:</h1>
      <CustomInput
        v-model="newTask"
        @keyup.enter="addTask()"
        class="taskInput"
        placeholder="Task here:"
      ></CustomInput>
      <button @click="addTask()" class="mainButton">Add Task</button>
      <h1>Tasks:</h1>
      <ul class="taskTable">
        <li v-for="(task, index) in tasks" :key="index" class="oneTask">
          <span class="taskText">{{ task }}</span>
          <button class="buttonDone" @click="taskDone()">Done</button>
        </li>
      </ul>
    </div>

    <div class="noteStack">
      <h1>Notes:</h1>
      <textarea
        v-model="newNote"
        @keyup.enter="addNote()"
        class="noteInput"
        spellcheck="false"
        placeholder="Note here:"
      ></textarea>
      <input
        v-model="newNoteName"
        type="text"
        name="noteName"
        class="noteName"
        placeholder="Note name here:"
        @keyup.enter="addNote()"
        maxlength="20"
      />
      <button @click="addNote()" class="mainButton">Add Note</button>
      <h2>Notes:</h2>
      <div class="noteBlock">
        <ul class="noteTable">
          <li
            v-for="(noteName, index) in noteNames"
            :key="index"
            class="noteList"
          >
            <div class="noteText" spellcheck="false">{{ noteName }}</div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>
