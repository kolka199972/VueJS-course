<template>
  <div class="card card-w70">
    <div v-if="isHasContent">
      <component
        v-for="property in properties"
        :key="property.id"
        :is="'View-' + property.type"
        :text="property.text"
      ></component>
    </div>
    <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>
import ViewTitle from './parts/ViewTitle.vue'
import ViewAvatar from './parts/ViewAvatar.vue'
import ViewSubtitle from './parts/ViewSubtitle.vue'
import ViewText from './parts/ViewText.vue'

export default {
  props: {
    properties: {
      type: Array,
      required: true
    }
  },
  computed: {
    isHasContent() {
      return Object.keys(this.properties).length > 0
    }
  },
  components: { ViewTitle, ViewAvatar, ViewSubtitle, ViewText }
}
</script>
