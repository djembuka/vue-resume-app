<template>
  <form class="card card-w30">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select id="type" v-model="type">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea id="value" rows="3" v-model="value"></textarea>
    </div>

    <button
      class="btn primary"
      :disabled="disabled"
      @click.prevent="clickButton"
    >
      Добавить
    </button>
  </form>
</template>

<script>
export default {
  name: 'AppForm',
  data() {
    return {
      type: 'title',
      value: '',
    };
  },
  computed: {
    disabled() {
      return this.value.length <= 3;
    },
  },
  emits: {
    'add-block'(blockObject) {
      if (blockObject && typeof blockObject === 'object') {
        return true;
      }
      return false;
    },
  },
  methods: {
    clickButton() {
      //add block
      this.$emit('add-block', {
        type: this.type,
        value: this.value,
        id: new Date().getTime(),
      });
      //reset form
      this.type = 'title';
      this.value = '';
    },
  },
};
</script>
