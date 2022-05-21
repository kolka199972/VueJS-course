<template>
   <div class="card" v-if="isValid">
      <h2>Комментарии</h2>
      <ul class="list" v-for="comment in comments" :key="comment.id">
        <li class="list-item">
          <div>
            <p><strong>{{ comment.email }}</strong></p>
            <small>{{ comment.body }}</small>
          </div>
        </li>
      </ul>
    </div>
    <p v-else><button class="btn primary" @click.prevent="$emit('loadComments')">Загрузить комментарии</button></p>
</template>

<script>
export default {
  props: {
    comments: {
      type: Array
    }
  },
  emits: ['loadComments'],
  computed: {
    isValid() {
      return this.comments.length > 0
    }
  }
}
</script>
