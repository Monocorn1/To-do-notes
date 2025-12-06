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
      if (this.newNote == "") {
      } else {
        this.notes.push(this.newNote);
        this.newNote = "";
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
      ></CustomInput>
      <button @click="addTask()" class="mainButton">Add Task</button>
      <ul class="taskTable">
        <li v-for="(task, index) in tasks" :key="index">
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
      ></textarea>
      <button @click="addNote()" class="mainButton">Add Note</button>
      <div class="noteBlock">
        <ul class="noteTable">
          <li v-for="(note, index) in notes" :key="index" class="noteList">
            <textarea class="noteText" spellcheck="false">{{ note }}</textarea>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>
