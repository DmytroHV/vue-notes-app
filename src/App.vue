<template>
  <div id="app">
    <div class="notes-section">
      <div class="columns">
        <div class="column has-text-centered">
          <strong>Notes</strong>
          <div v-for="note in notes" :key="note" class="notes">
            {{ note }}
          </div>
        </div>
        <div class="column has-text-centered">
          <strong>Timestamp</strong>
          <div v-for="timestamp in timestamps" :key="timestamp" class="timestamps">
            {{ timestamp }}
          </div>
        </div>
      </div>
      <input-component :placeholder="placeholder" @add-note="addNote"></input-component>
    </div>
    <note-count></note-count>
  </div>
</template>

<script>
import InputComponent from "./components/InputComponent.vue";
import NoteCount from "./components/NoteCount.vue";

export default {
  name: "app",
  data() {
    return {
      notes: [],
      timestamps: [],
      placeholder: "Enter a note"
    };
  },
  components: {
    "input-component": InputComponent,
    "note-count": NoteCount
  },
  methods: {
    addNote(event) {
      this.notes.push(event.note);
      this.timestamps.push(event.timestamp);
    }
  }
};
</script>

<style lang="scss">
html,
body {
  height: 100%;
}

#app {
  height: inherit;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  -webkit-align-items: center;
  justify-content: center;
  -webkit-justify-content: center;
}

.notes-section {
  width: 500px;
}

.columns {
  width: 100%;
}

.notes,
.timestamps {
  padding: 5px 0px;
}

.note-count {
  margin-top: 48px;
}
</style>
