<template>
  <div class="form">
    <!-- <div class="form__group">
      <label class="form__label" for="value">Виберіть тип операції:</label>
      <select class="form__select" name="" id="status" v-model='formData.status'>
        <option value="income">Дохід</option>
        <option value="outcome">Розхід</option>
      </select>
    </div> -->
    <div class="form__group">
      <label class="form__label" for="value">Введіть сумму:</label>
      <input class="form__input" id="value" type="text" placeholder="Сумма" v-model='formData.value'>
    </div>
    <div class="form__group">
      <label class="form__label" for="comment">Введіть коментарій:</label>
      <input class="form__input" id="comment" type="text" placeholder="Коментарій" v-model='formData.comment'>
    </div>
    <input class="form__button" @click.prevent='getFormData' type="button" value="Додати запис">
  </div>
</template>

<script>
export default {
  name: 'Form',

  props: {

  },

  data: () => ({
    formData: {
      status: 'INCOME',
      comment: '',
      value: 0,
    },
  }),

  methods: {
    getFormData() {
      this.$emit('getFormData', { ...this.formData });
    },
  },
};

</script>

<style lang="scss">
  .form {
    display: flex;
    flex-direction: column;
    max-width: 500px;
    align-items: flex-start;
    margin: 50px auto;
    padding: 0 40px;

    &__select, &__input {
      width: 100%;
      box-sizing: border-box;
      margin-top: 3px;
    }

    &__input {
      padding: 5px 10px;
      border: none; /* <-- This thing here */
      border:solid 1px #000;
      border-radius: 10px;
      line-height: 28px;
    }

    &__group {
      width: 100%;
      text-align: start;
      margin: 5px 0
    }

    &__label {
      font-size: 18px;
      font-weight: bold;
    }

    &__button {
      width: 170px;
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
