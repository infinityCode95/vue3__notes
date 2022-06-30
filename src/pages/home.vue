<template>
   <div class="home">
      <div class="home__container">
         <NotesForm @onSubmit="handleSubmit" />
         <NotesList @onRemove="handleRemove" :items="notes" />
      </div>
   </div>
</template>

<script>
import NotesForm from '@/Components/Notes/NotesForm.vue';
import NotesList from '@/Components/Notes/NotesList.vue';

export default {
   components: {NotesForm, NotesList},

   data() {
      return {
         notes: [
            {
               title: 'Note one',
            },
            {
               title: 'Note two',
            },
         ]
      }
   },

   mounted() {
      this.getNotes();
   },

   watch: {
      notes: {
         handler(updatedList) {
            localStorage.setItem('notes', JSON.stringify(updatedList))
         },
         deep: true
      }
   },
   
   methods: {
      getNotes() {
         const localNotes = localStorage.getItem('notes')
         if (localNotes) {
            this.notes = JSON.parse(localNotes)
         }
      },

      handleSubmit(value) {
         const newNote = {
            title: value,
         }
         this.notes.push(newNote)
      },
      
      handleRemove(index) {
         this.notes.splice(index, 1)
      },
   }
}
</script>