<template>
  <section class="tree">
    <ul class="tree-list">
      <treeview-item :treeview="treeviewList"></treeview-item>
    </ul>
  </section>
</template>

<script>
import TreeviewItem from "@/components/TreeviewItem";

export default {
  name: 'treeview-list',

  props: {
    treeviewList: Object
  },
  components: {
    TreeviewItem
  }
};
</script>
