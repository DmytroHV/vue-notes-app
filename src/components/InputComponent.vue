<template>
  <input
    class="input is-small"
    type="text"
    :placeholder="placeholder"
    v-model="input"
    @keyup.enter="handleEnterKey"
  />
</template>

<script>
import { EventBus } from "@/main.js";

export default {
  name: "InputComponent",
  props: {
    placeholder: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      input: ""
    };
  },
  methods: {
    handleEnterKey() {
      this.$emit("add-note", {
        note: this.input,
        timestamp: new Date().toLocaleString()
      });
      EventBus.$emit("note-count-increased");
      this.input = "";
    }
  }
};
</script>