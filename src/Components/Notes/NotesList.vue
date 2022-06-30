<template>
   <div class="notes__list">
      <div class="note__item" v-for="(note, index) in items" :key="index">
         <div class="note__body">
            <p>{{note.title}}</p>             
            <i @click="onRemove(index)" class="note__icon fa-solid fa-trash fa-lg"></i>
         </div>
      </div>
   </div>
</template>

<script>

export default {
   props: {
      items: {
         type: Array,
         required: true,
      }
   },
   
   methods: {
      onRemove() {
         this.$emit('onRemove', this.index)
      },
   }
}
</script> 