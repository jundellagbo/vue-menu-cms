<template>
  <div id="app">
    <button @click="addMenu">add menu</button>
    <vue-menu-cms ref="menucms" v-model="tree" />
    <pre>
      {{tree}}
    </pre>
  </div>
</template>
<script>
import './assets/style.scss'
import VueMenuCms from './MenuCms.vue'

const treeObject = () => ({
  title: ``,
  slug: ``,
  attrs: ``,
  menus: [],
  order: Date.now()
})

export default {
  components: {
    VueMenuCms
  },
  data: () => ({
    tree: {
      menus: [treeObject()]
    }
  }),
  methods: {
    addMenu() {
      this.$refs.menucms.addMenu()
    }
  }
}
</script>