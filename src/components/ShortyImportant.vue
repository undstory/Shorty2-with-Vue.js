<template>
    <div>
         <a href="#" class="add__btns add__btn--important link" @click="giveMeImportant" >
                    Important
                   {{ howManyImportant }}
                </a>
    </div>
</template>

<script>
export default {
    name: 'shorty-important',
    props: {
         notes: {
             type: Array,
             require: true 
         }
    },

    computed: {
          howManyImportant() {
                return this.notes.filter(note => note.important).length;
            },
    },

    methods: {
        giveMeImportant() {
            console.log(this.notes.filter(note => note.important));
        }
    }
       
    
}
</script>