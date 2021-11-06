<template>
  <div class="container column">
    <app-form @addBlock="addBlock"></app-form>

    <app-body :blocks="blocks"></app-body>
  </div>
  <div class="container">
    <app-comments></app-comments>
  </div>
</template>

<script>
import AppForm from './AppForm.vue';
import AppBody from './AppBody.vue';
import AppComments from './AppComments.vue';

export default {
  data() {
    return {
      blocks: [],
    };
  },
  methods: {
    addBlock(blockObject) {
      this.blocks.push(blockObject);
    },
  },
  components: {
    AppForm,
    AppBody,
    AppComments,
  },
};
</script>

<style>
.avatar {
  display: flex;
  justify-content: center;
}

.avatar img {
  width: 150px;
  height: auto;
  border-radius: 50%;
}
</style>
