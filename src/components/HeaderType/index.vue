<template>
  <div class="header-type">
    <div
      class="item"
      :class="{ active: index === activeIndex }"
      v-for="(item, index) in types"
      :key="item.id"
      @click="handleClick(item, index)"
    >
      {{ item.description }}
    </div>
  </div>
</template>

<script>
export default {
  name: "HeaderType",
  props: {
    types: {
      type: Array,
      default() {
        return [];
      }
    }
  },
  data() {
    return { activeIndex: 0 };
  },
  methods: {
    handleClick(data, index) {
      this.activeIndex = index;
      this.$emit("click", { data, index });
    }
  }
};
</script>

<style lang="scss" scoped>
@import "~@/assets/styles/mixins.scss";
.header-type {
  display: flex;
  flex-wrap: wrap;
  padding: 10px 0;
  @include border-bottom;
  .item {
    width: 20%;
    font-size: 14px;
    line-height: 24px;
    text-align: center;
    color: #000;
    &.active {
      color: #e7370c;
    }
  }
}
</style>
