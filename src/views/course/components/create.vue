<template>
  <create-or-edit/>
</template>

<script lang="ts">
import Vue from 'vue'
import CreateOrEdit from './CreateOrEdit.vue'
export default Vue.extend({
  name: 'CourseCreate',
  components: { CreateOrEdit }
})
</script>
<style lang="scss" scoped></style>
