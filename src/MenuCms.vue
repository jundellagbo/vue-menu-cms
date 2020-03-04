<template>
  <div class="vue-menu-cms-">
    <vue-cms-menu-nested :menus="tree.menus" @removeField="(orderKey) => removeField(orderKey)" />
  </div>
</template>

<script>
import VueCmsMenuNested from "./MenuCms/MenuCmsNested.vue";

const treeObject = () => ({
  title: ``,
  slug: ``,
  attrs: ``,
  menus: [],
  order: Date.now()
})

export default {
    name: 'vue-cms-menu-component',
    props: {
        logger: {
            type: Boolean,
            default: false
        },
        value: {
            type: Object,
            default: () => ({ 
                menus: [treeObject()]
            })
        }
    },
    components: {
        VueCmsMenuNested
    },
    methods: {
        addMenu() {
            this.tree.menus.push(treeObject())
        },
        removeField(orderKey) {
            this.removeTree(this.tree, orderKey)
        },
        removeTree(parent, orderKey) {
            const e = this
            parent.menus = parent.menus.filter(menu => menu.order !== orderKey)
            .map(menu => e.removeTree(menu, orderKey))
            return parent
        }
    },
    data() {
        return {
            tree: {
                menus: []
            }
        }
    },
    mounted() {
        this.tree = this.value
    },
    watch: {
        tree: {
            handler(value) {
                this.$emit('input', value)
            },
            deep: true,
            immediate: true
        }
    }
};
</script>