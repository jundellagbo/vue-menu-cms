<template>
    <div class="vue-cms-menu-fields">
        <input v-model="field.title" placeholder="Enter Menu Name" class="vue-cms-input" />
        <input v-model="field.slug" placeholder="Enter slug / url" class="vue-cms-input" />
        <input v-model="field.attrs" placeholder="Enter Menu Attributes" class="vue-cms-input" />
        <small>Separated by comma ex: target=_blank,id=my-menu-id,class=my-menu-classname</small>
    </div>
</template>
<script>
export default {
  props: {
    field: {
      type: Object
    }
  }  
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