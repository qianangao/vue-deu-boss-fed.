<template>
  <course-list></course-list>
</template>

<script lang="ts">
import Vue from 'vue'
import CourseList from './components/List.vue'
export default Vue.extend({
  name: 'CourseIndex',
  components: { CourseList }
})
</script>

<style lang="scss" scoped></style>
