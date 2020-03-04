# Vue Menu CMS

```
npm i @jundell/vue-menu-cms
```

### Markup

```
<template>
    <div>
        <button @click="addMenu">Add Menu</button>
        <vue-menu-cms ref="menucms" v-model="tree" />
        <pre>
        {{ tree }}
        </pre>
    </div>
</template>
<script>
import '@jundell/vue-menu-cms/src/assets/style.scss';
import VueMenuCms from '@jundell/vue-menu-cms/src/MenuCms.vue';
const treeObject = () => ({
  title: '',
  slug: '',
  attrs: '',
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
```

also works with Nuxt.js plugins


```
vue-menu-cms.js
```

```
import Vue from 'vue';
import '@jundell/vue-menu-cms/src/assets/style.scss';
import VueMenuCms from '@jundell/vue-menu-cms/src/MenuCms.vue';

Vue.component('VueMenuCms', VueMenuCms);
```

------

```
nuxt.config.js
```

```
plugins: [
    { src: 'myplugin-dir/vue-menu-cms', ssr: false }
]
```

### Overide SCSS Variables

```
variables.scss
```

```
$pcolor: red;
$rcolor: grey;
$scolor: blue;
```

```
import 'variables.scss';
import '@jundell/vue-menu-cms/src/assets/style.scss';
```