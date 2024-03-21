<template>
  <div class="modal">
    <h1 id="header" v-if="uiState === 'won'">You've won!</h1>
    <h1 id="header" v-else>You've lost!</h1>
    <Face :frown="uiState !== 'won'" />
    <button class="button" @click="resetGame">Let's play again</button>
  </div>
</template>

<script>
import { mapState } from 'vuex';
import Face from './Face.vue';
export default {
  components: {
    Face,
  },
  methods: {
    resetGame() {
      this.$store.commit('resetGame');
    },
  },
  computed: {
    ...mapState(['uiState']),
  },
};
</script>

<style scoped lang="scss">
.modal {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
