<template>
  <template v-if="itemsLength">
    <div class="list">
    <div class="list__item" v-for="(item, index) in items" :key="index">
      <span class="budget-comment list__comment">{{ item.comment }}</span>
      <span class="budget-value list__value">{{ item.value }}</span>
      <button class="list__button" @click="deleteItem(item)">Delete</button>
    </div>
  </div>
  </template>
  <template v-else>
    <h2>У вас поки нема записів...</h2>
  </template>
</template>

<script>
export default {
  name: 'List',

  props: {
    items: {
      type: Array,
      default: () => ([]),
    },
  },

  methods: {
    deleteItem(id) {
      this.$emit('deleteItem', id);
    },
  },

  data: () => ({
    length: 0,
  }),

  computed: {
    itemsLength() {
      return this.items.length;
    },
  },

};

</script>

<style lang="scss">
  .list {
    max-width: 500px;
    margin: auto;

    &__item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      border: 3px solid gray;
      border-radius: 15px;
      padding: 0 20px;
      background-color: moccasin;
    }

    &__value {
      margin-left: auto;
      margin-right: 20px;
      align-content: center;
      font-weight: bold;
    }

    &__button {
      width: 70px;
      height: 40px;
      background: #ff0000;
      border: 3px solid #000000;
      outline: none;
      border-radius: 15px;
      margin: 10px 0;

      &:hover {
        cursor: pointer;
        box-shadow: 0 0 10px rgba(0,0,0,1);
      }
    }
  }
</style>
