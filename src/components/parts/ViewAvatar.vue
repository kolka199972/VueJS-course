<template>
  <div class="avatar">
    <!-- <img src="https://cdn.dribbble.com/users/5592443/screenshots/14279501/drbl_pop_r_m_rick_4x.png"> -->
    <img :src="text">
  </div>
</template>

<script>
export default {
  props: {
    text: {
      type: String,
      required: true,
      validator(str) {
        return str.includes('https:')
      }
    }
  }
}
</script>
