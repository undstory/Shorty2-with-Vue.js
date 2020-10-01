<template>
    <div>
        <a href="#" class="add__btns add__btn--archive link" @click="giveMeArchive">
                    Archive
                   {{ howManyArchive }}
                </a>
    </div>
</template>

<script>
export default {
    name: 'shorty-archive',
    props: {
         notes: {
             type: Array,
             require: true 
         }
    },

    computed: {
          howManyArchive() {
                return this.notes.filter(note => note.archive).length;
            },
    },

    methods: {
        giveMeArchive() {
            console.log(this.notes.filter(note => note.archive));
        }
    }
       
    
}
</script>