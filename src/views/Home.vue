<template>
  <div class="content container flex">
    <div class="content_card card">
      <div class="card_header">
        <h4>The treeview</h4>
      </div>
      <div class="card_text">
        <treeview-list :treeviewList="treeview"></treeview-list>
      </div>
    </div>

    <div class="content_card card">
      <div class="card_header">
        <h4>The list</h4>
      </div>
      <list v-if="list.length > 0" :list="list" @remove="remove($event)" />
      <p v-else class="text-center card_text">Список пустой</p>
    </div>
  </div>
</template>

<script>
import TreeviewList from "@/components/TreeviewList.vue";
import List from "@/components/List";

class Item {
  constructor(name, selected) {
    (this.name = name), (this.selected = selected);
  }
}

export default {
  name: "Home",

  components: {
    TreeviewList,
    List,
  },

  computed: {
    list() {
      let res = [];

      function recourse(childred) {
        for (let i in childred) {
          if (typeof childred[i] == "object") {
            let item = new Item(childred[i].name, childred[i].selected);
            res.push(item);

            if (childred[i].childred && childred[i].childred.length > 0) {
              recourse(childred[i].childred);
            }
          }
        }
      }

      if (typeof this.treeview == "object") {
        let item = new Item(this.treeview.name, this.treeview.selected);
        res.push(item);

        if (this.treeview.childred && this.treeview.childred.length > 0) {
          recourse(this.treeview.childred);
        }
      }
      return res.filter((item) => item.selected == true);
    },
  },

  data() {
    return {
      treeview: {
        name: "root",
        selected: true,
        childred: [
          {
            name: "item1",
            selected: true,
            childred: [
              { name: "item2", selected: true },
              {
                name: "item3",
                selected: true,
                childred: [
                  { name: "item4", selected: true },
                  { name: "pian", selected: true },
                ],
              },
            ],
          },
          { name: "item5", selected: true },
          {
            name: "item6",
            selected: true,
            childred: [
              { name: "item7", selected: true },
              { name: "item8", selected: true },
              {
                name: "item9",
                selected: true,
                childred: [
                  { name: "item10", selected: true },
                  { name: "item11", selected: true },
                ],
              },
            ],
          },
        ],
      },
    };
  },

  methods: {
    remove(item) {
      function unchecked(item, childred) {
        for (let i in childred) {
          if (typeof childred[i] == "object") {
            if (childred[i].name === item.name) {
              childred[i].selected = item.selected;
            }

            if (childred[i].childred && childred[i].childred.length > 0) {
              unchecked(item, childred[i].childred);
            }
          }
        }
      }

      if (typeof this.treeview == "object") {
        if (this.treeview.name === item.name) {
          this.treeview.selected = item.selected;
        }

        if (this.treeview.childred && this.treeview.childred.length > 0) {
          unchecked(item, this.treeview.childred);
        }
      }
    },
  },
};
</script>


