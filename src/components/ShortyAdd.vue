<template>
    <section class="add">
        <div class="add__wrapper">
            <form class="add__form" action="#">
                <textarea class="add__textarea"
                 rows="11"
                 cols="28"
                 placeholder="// Write something you want to remember..."
                 v-model="newNote"
                 ></textarea>
                 <button class="add__btn" @click="addNote"><i class="fas fa-plus"></i></button>
            </form>
            <div class="item__wrapper">
                <shorty-item v-for="note in notes" :key="note.id" v-bind:note="note">
                <!-- <div>{{ note.text }} </div> -->

            </shorty-item>
            </div>
            
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
            noteId: 3,
            notes: [
                {
                'id': 1,
                'text': 'Zajebiście ciekawa rzecz',
                'deleted': false
            }, 
                {
                'id': 2,
                'text': "Kolejna wykurwista rzecz",
                'deleted': false
            }]
        }
    },
    methods: {
        addNote() {
       
            this.notes.push({
                id: this.noteId,
                text: this.newNote,
                deleted: false
            })

            this.newNote = '',
            this.noteId++;
        }
    }
}
</script>

<style lang="scss">
    .add {
        margin: 5rem 0;
        &__form {
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        &__textarea {
            resize: none;
            padding: .8rem;
            font-size: 1.5rem;
            margin-bottom: 2rem;
            background-color: #E0DFE0;
            border: none;
            border-radius: 10px;

            
        }

        &__btn {
            border-radius: 10px;
            border: none;
            background-color: #E0DFE0;
            cursor: pointer;
            
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
            justify-content: space-between;
            border: 1px solid red;
            margin: 3rem 1%;
        }
    }
</style>