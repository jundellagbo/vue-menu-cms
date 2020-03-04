<template>
  <draggable class="vue-cms-menu-dragarea" tag="ul" :list="menus" :group="{ name: 'g1' }" v-bind="dragOptions">
    <li v-for="(el, index) in menus" :key="el.order">
        <menu-fields :field="el" />
        <button v-if="!(!issub && index==0)" class="vue-cms-btn danger small btn-remove" @click="$emit('removeField', el.order)">Remove Field</button>
        <vue-cms-menu-nested-draggable :menus="el.menus" :issub="true" class="submenus" @removeField="orderKey => $emit('removeField', orderKey)"  />
    </li>
  </draggable>
</template>
<script>
import draggable from "vuedraggable";
import MenuFields from './MenuFields.vue'
export default {
  props: {
    menus: {
      required: true,
      type: Array
    },
    issub: {
        type: Boolean,
        default: false
    }
  },
  components: {
    draggable,
    MenuFields
  },
  name: "vue-cms-menu-nested-draggable",
  computed: {
    dragOptions() {
      return {
        animation: 0,
        group: "description",
        disabled: false,
        ghostClass: "vue-cms-menu-ghost"
      };
    }
  }
};
</script>
<style lang="scss" scoped>
.vue-cms-menu-dragarea {
  min-height: 100px;
  background: #fbfbfb;
  list-style: none;
  margin-bottom: 5px;
  outline: 1px dashed;
  padding-top: 15px;
  .vue-cms-menu-note {
      display: block;
      margin-bottom: 10px;
  }
  .btn-remove {
      margin-bottom: 10px;
  }
    &.submenus {
        padding-left: 50px;
    }
    li {
        cursor: move;
    }
}
.vue-cms-menu-ghost {
  opacity: 0.5;
  background: #c8ebfb;
  cursor: move;
}
</style>