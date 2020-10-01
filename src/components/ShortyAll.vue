<template>
    <div>
         <a href="#" class="add__btns add__btn--archive link" @click="giveMeAll">
                    All Notes
                   {{ howManyAllNotes}}
                </a>
    </div>
</template>

<script>
export default {
    name: 'shorty-all',
    props: {
         notes: {
             type: Array,
             require: true 
         }
    },
  

 computed: {
          howManyAllNotes() {
                return this.notes.length;
            },
    },

    methods: {
        giveMeAll() {
            console.log(this.notes);
        }
    }
       
    
}
</script>

<style>


    
</style>