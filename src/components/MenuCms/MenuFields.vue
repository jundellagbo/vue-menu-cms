<template>
    <div class="vue-cms-menu-fields">
        <input v-model="field.title" placeholder="Enter Menu Name" class="vue-cms-input" />
        <input v-model="field.slug" placeholder="Enter slug / url" class="vue-cms-input" />
        <input v-model="field.target" placeholder="Enter url target - optional" class="vue-cms-input" />
    </div>
</template>
<script>
export default {
  props: ['field']  
}
</script>
<style lang="scss" scoped>
.vue-cms-menu-fields {
  background: #ececec;
  padding: 20px;
  border-radius: 4px;
  margin-bottom: 15px;
}
</style>