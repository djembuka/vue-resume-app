<template>
  <div class="avatar">
    <img :src="value" />
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      required: true,
    },
  },
  name: 'AppBodyAvatar',
};
</script>
