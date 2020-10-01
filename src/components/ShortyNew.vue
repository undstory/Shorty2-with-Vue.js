<template>
    <div>
          <a href="#" class="add__btns add__btn--archive link" @click="giveMeNew">
                    New Notes
                   {{ howManyNewNotes}}
                </a>
    </div>
</template>

<script>
export default {
    name: 'shorty-new',
    props: {
         notes: {
             type: Array,
             require: true 
         }
    },
    data() {
        return {
            filterQuery: {
                'important': false,
                'archive': false
            },
            filteredNotes: []
        }
    },

    computed: {
        // giveMeNew() {
        //     return this.filteredNotes = this.notes.filter(note => Object.keys(this.filterQuery).every(key => note[key] === this.filterQuery[key]));
           
        // },
          howManyNewNotes() {
                return this.notes.filter(note => Object.keys(this.filterQuery).every(key => note[key] === this.filterQuery[key])).length;
            },
    },

    methods: {
        giveMeNew() {
             this.filteredNotes = this.notes.filter(note => Object.keys(this.filterQuery).every(key => note[key] === this.filterQuery[key]));
             console.log(this.filteredNotes);
             return this.filteredNotes;
        }
    }
       
    
}
</script>