<template>
  <div id="app">
    <button @click="$refs['menu-cms'].addMenu()">add menu</button>
    <vue-menu-cms ref="menu-cms" v-model="tree" />
    <pre>
      {{tree}}
    </pre>
  </div>
</template>
<script>
import './assets/style.scss'
import VueMenuCms from './components/MenuCms.vue'
import { menuObj } from './helpers/menu'
export default {
  components: {
    VueMenuCms
  },
  data: () => ({
    tree: {
      menus: [menuObj()]
    }
  })
}
</script>