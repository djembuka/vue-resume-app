<template>
  <div class="card card-w70">
    <div v-if="blocks.length">
      <div v-for="block in blocks" :key="block.id">
        <component
          :is="`app-body-${block.type}`"
          :value="block.value"
        ></component>
      </div>
    </div>
    <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>
import AppBodyTitle from './AppBodyTitle.vue';
import AppBodyAvatar from './AppBodyAvatar.vue';
import AppBodySubtitle from './AppBodySubtitle.vue';
import AppBodyText from './AppBodyText.vue';

export default {
  props: {
    blocks: {
      type: Array,
      required: false,
      default() {
        return [];
      },
    },
  },
  name: 'AppCard',
  components: {
    AppBodyTitle,
    AppBodyAvatar,
    AppBodySubtitle,
    AppBodyText,
  },
};
</script>
