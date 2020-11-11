<template>
  <div class="modal">
    <!-- exercise -->
    <!-- different info & svg based on won or lost state -->
    <div>
      <h2 v-if="uiState === 'won'">You won</h2>
      <h2 v-else>You lost</h2>
    </div>
    <!-- always able to restart game -->
    <button @click="restart">Restart?</button>
  </div>
</template>

<script>
import { mapState } from "vuex";

export default {
  computed: {
    ...mapState(["uiState"]),
  },
  methods: {
    restart() {
      // set score to 0, set question index to 0, set character to empty string, set ui state to start
      this.$store.commit("updateScore", 0);
      this.$store.commit("resetQuestionIndex");
      this.$store.commit("updateCharacter", "");
      this.$store.commit("updateUIState", "start");
    },
  },
};
</script>

<style lang="scss" scoped></style>
