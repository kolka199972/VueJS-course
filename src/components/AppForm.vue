<template>
  <form class="card card-w30">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select id="type" v-model="selected">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea id="value" rows="3" v-model="text"></textarea>
    </div>

    <button
      class="btn primary"
      @click.prevent="addInformation"
      :disabled="isValid"
    >Добавить</button>
  </form>
</template>

<script>
export default {
  emits: {
    loadInformation(properties) {
      if (typeof properties === 'object') {
        return true
      }
      return false
    }
  },
  data() {
    return {
      selected: 'title',
      text: ''
    }
  },
  methods: {
    addInformation() {
      this.$emit('loadInformation', {
        type: this.selected,
        text: this.text,
        id: Date.now()
      })
      this.selected = 'title'
      this.text = ''
    }
  },
  computed: {
    isValid() {
      return this.text.length <= 3
    }
  }
}
</script>
