# Vue Menu CMS

A content management system for menu.

![](https://raw.githubusercontent.com/jundellagbo/vue-menu-cms/master/cms.gif)

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
export default {
  components: {
    VueMenuCms
  },
  data: () => ({
      tree: {
          menus: [
            {
              title: '',
              slug: '',
              attrs: '',
              menus: [],
              order: Date.now()
            }
          ]
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

------

also works with Nuxt.js plugins


```
plugins/vue-menu-cms.js
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
module.exports = {
  plugins: [
      { src: '~/plugins/vue-menu-cms', ssr: false }
  ]
}
```

------

### Overide SCSS Variables

```
$pcolor: red; // primary
$rcolor: grey; // red
$scolor: blue; // secondary
```

```
import 'variables.scss';
import '@jundell/vue-menu-cms/src/assets/style.scss';
```