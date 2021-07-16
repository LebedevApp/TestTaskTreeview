<template>
  <li class="node-tree">
    <input class="checkbox" type="checkbox" v-model="treeview.selected" :id='treeview.name' />
    <label :for="treeview.name" class="label">{{ treeview.name }}</label>
   

    <ul v-if="treeview.childred && treeview.childred.length">
      <treeview v-for="(child, i) in treeview.childred" :key="i" :treeview="child"></treeview>
    </ul>
  </li>
</template>

<script>
export default {
  name: "treeview",

  props: {
    treeview: Object,
  },
};
</script>
