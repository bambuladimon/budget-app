<template>
  <div id="balance">
    <h1 >Ваш баланс {{ total }}</h1>
  </div>
</template>

<script>
export default {
  name: 'Balance',
  props: ['total'],
};

</script>

<style lang="scss">

</style>
