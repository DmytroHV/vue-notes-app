<template>
  <div class="note-count">
    Note count: <strong>{{ count }}</strong>
  </div>
</template>

<script>
import { EventBus } from "@/main.js";

export default {
  data() {
    return {
      count: 0
    };
  },
  created() {
    EventBus.$on("note-count-increased", () => this.count++);
  }
};
</script>
