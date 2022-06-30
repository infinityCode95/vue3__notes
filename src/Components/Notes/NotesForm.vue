<template>
   <div class="form__wrapper">
      <form class="form" @submit.prevent="onSubmit">
         <input class="form__input" type="text" required v-model="value" placeholder="Введите текст">
         <button class="form__btn" type="submit">Добавить</button>
      </form>
   </div>
</template>

<script>

export default {

   data() {
      return {
         value: '',
      }
   },
   
   methods: {
      onSubmit () {
         this.$emit('onSubmit', this.value)
         this.value = ''
      },
   }
}
</script>
