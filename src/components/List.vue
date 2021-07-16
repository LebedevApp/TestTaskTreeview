<template>
  <section>
    <div class="card_text text-center">
      <div v-for="(item, i) in list" :key="i" class="element">
        <div class="list-item flex">
          <span class="item-name">{{ item.name }}</span>
          <button class="button" @click="remove(item)">REMOVE</button>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "list-item",

  props: {
    list: {
      type: Array,
    },
  },

  methods: {
    remove(item) {
      item.selected = false;
      this.$emit("remove", item);
    },
  },
};
</script>

<style lang="scss" scoped>
.item-name{
  min-width: 150px;
}
</style>

