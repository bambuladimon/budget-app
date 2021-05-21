<template>
  <div id="app">
    <Total :total='totalSum'/>
    <Form @getFormData="onSubmit" />
    <List :items='items' @deleteItem="onDeleteItem"/>
  </div>
</template>

<script>
import Form from './components/Form.vue';
import List from './components/List.vue';
import Total from './components/Total.vue';

export default {
  name: 'App',
  components: {
    Form,
    List,
    Total,
  },

  data: () => ({
    total: 0,
    items: [],
  }),

  mounted() {
    if (localStorage.getItem('items')) {
      try {
        this.items = JSON.parse(localStorage.getItem('items'));
      } catch (e) {
        localStorage.removeItem('items');
      }
    }
  },

  methods: {
    onDeleteItem(id) {
      this.items.splice(this.items.indexOf(id), 1);
      this.saveItems();
    },
    onSubmit(data) {
      if (data.comment === '') {
        return;
      }
      this.items.push({
        comment: data.comment,
        value: Number(data.value),
        id: Math.random,
        status: data.status,
      });
      this.saveItems();
    },
    saveItems() {
      const parsed = JSON.stringify(this.items);
      localStorage.setItem('items', parsed);
    },
  },

  computed: {
    totalSum() {
      return this.items.reduce((total, item) => total + item.value, 0);
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
