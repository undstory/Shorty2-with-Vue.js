<template>
    <section class="add">
        <div class="add__wrapper">
            <form class="add__form" action="#">
                <textarea class="add__textarea"
                 rows="11"
                 cols="28"
                 placeholder="// Write something you want to remember..."
                 v-model="newNote"
                 @keyup.enter="addNote"
                 ></textarea>
                 <button class="add__btn" @click="addNote"><i class="fas fa-plus"></i></button>
            </form>
            <div class="add__summary">
                <h2>Summary:</h2>
                 <button class="add__btns add__btn--all">
                    <span class="add__btns--info">New Notes</span>
                    <span class="add__btns--how">{{ howManyNewNotes }}</span>
                </button>
                <button class="add__btns add__btn--important" >
                    <span class="add__btns--info">Important</span>
                    <span class="add__btns--how">{{ howManyImportant }}</span>
                </button>
                <button class="add__btns add__btn--archive">
                    <span class="add__btns--info">Archive</span>
                    <span class="add__btns--how">{{ howManyArchive }}</span>
                </button>
                <button class="add__btns add__btn--all">
                    <span class="add__btns--info">All Notes</span>
                    <span class="add__btns--how">{{ howManyNotes }}</span>
                </button>
            </div>
        </div>
            <div class="item__wrapper">
                <shorty-item v-for="(note, index) in notes" :key="note.id" v-bind:note="note" v-bind:index="index" @removedItem="removeItem(index)"
                @finishedEdit="finishedEdit" @importantOrNot="importantOrNot" @archiveOrNot="archiveOrNot">
                <!-- <div>{{ note.text }} </div> -->

            </shorty-item>
            </div>
            
        
    </section>
</template>

<script>

import ShortyItem from './ShortyItem.vue'

export default {
    name: "shorty-add",
    components: {
        ShortyItem
    },
    data() {
        return {
            newNote: '',
            filter: "all",
            noteId: 3,
            // beforeEdit: '',
            notes: [
                {
                'id': 1,
                'text': 'Zajebiście ciekawa rzecz',
                'editing': false,
                'important': false,
                'archive': false
            }, 
                {
                'id': 2,
                'text': "Kolejna wykurwista rzecz",
                'editing': false,
                'important': false,
                'archive': false
            }]
        }
    },

    computed: {
            // notesFiltered() {
            //     if(this.filter == 'all') {
            //         return this.notes;
            //     } else if(this.filter == 'important') {
            //         return this.notes.filter(note => note.important);
            //     }

            //     return this.notes;
            // },

            howManyNotes() {
                return this.notes.length;
            },

            howManyNewNotes() {
                return this.notes.length;
            },

            howManyImportant() {
                return this.notes.filter(note => note.important).length;
            },

             howManyArchive() {
                return this.notes.filter(note => note.archive).length;
            }
    },
    methods: {
        addNote() {
            if(this.newNote.trim().length == 0) {
                alert("You have to write something...");
                return;
                
            }
            this.notes.push({
                id: this.noteId,
                text: this.newNote,
                editing: false,
                important: false,
                archive: false
            })

            this.newNote = '',
            this.noteId++;
        },

   
        
        removeItem(index) {
            this.notes.splice(index, 1);
        },

        finishedEdit(data) {
            this.notes.splice(data.index, 1, data.note);
        },

        importantOrNot(data) {
            this.notes.splice(data.index, 1, data.note);
           
        },

        archiveOrNot(data) {
            this.notes.splice(data.index, 1, data.note);
        }
    }
}
</script>

<style lang="scss">
    .add {
        margin: 5rem 0;
        &__form {
            display: flex;
            flex-direction: row;
            align-items: center;
        }

        &__wrapper {
            display: flex;
            flex-direction: row;
            justify-content: center;
        }

        &__summary {
            margin-left: 1rem;
            align-self: center;
        }

        &__btns {
            padding: .5rem;
            font-size: 1.2rem;
            color: #175242;
            font-weight: bold;
            letter-spacing: 1px;
            border-radius: 10px;
            border: none;
            background-color: #E0DFE0;
            cursor: pointer;
            margin: 1rem;
            min-width: 8.5rem;

            &:hover {
                color: #E0DFE0;
                background-color: #6C446B;
            }

            &--info, &--how {
                display: block;
                padding-bottom: .5rem;
            }

            &--info{
                padding-top: .5rem;
            }


        }

        &__textarea {
            resize: none;
            padding: .8rem;
            font-size: 1.5rem;
            margin-bottom: 2rem;
            margin-right: 1rem;
            background-color: #E0DFE0;
            border: none;
            border-radius: 10px;
        }

        &__btn {
            border-radius: 10px;
            border: none;
            background-color: #E0DFE0;
            cursor: pointer;
            align-self: flex-start;
            
            i {
                font-size: 2.5rem;
                padding: .8rem;
                color: #175242;
                border-radius: 10px;

                &:hover {
                    color: #E0DFE0;
                }
            }

            &:hover {
                background-color: #6C446B
            }
        }
    }

    .item {
        &__wrapper {
            display: flex;
            flex-direction: row;
            flex-wrap: wrap;
            justify-content: center;
            margin: 3rem 1rem;
        }
    }
</style>