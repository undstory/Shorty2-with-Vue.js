<template>
    
        <div class="item"  v-bind:class="{'item--active': important, 'item--archive': archive}" >
            <div class="item__up">
                <template>
                    <div class="item__text" @dblclick="editItem" v-if="!editing">{{ text }}</div>
                    <textarea wrap="on" class="item__text--edit" v-else
                    v-model="text" rows="5" cols="15" 
                    @blur="doneEdit"
                    @keyup.enter="doneEdit"
                    @keyup.esc="cancelEdit"
                    v-focus maxlength="50"></textarea>
                </template>
                
                <button class="item__btn--important" @click="thisIsImportant">
                    <i class="fas fa-bell item__bell" v-bind:class="{'item__bell--active': important, 'btn__desactive': archive }"></i></button>
            </div>
            <div class="item__down">
                 <span class="item__date">{{ currentDate | niceDate }}</span>
                 <div class="item__btns">
                     <button class="item__btn--archive" @click="addToArchive" v-bind:class="{'btn__desactive': important }"><i class="fas fa-plus-circle item__archive"></i></button>
                     <button class="item__btn--remove" @click="removeItem(index)" v-bind:class="{'btn__desactive': important }"><i class="fas fa-trash item__remove"></i></button>
                 </div>
            </div>
           
        </div>
    
</template>

<script>
export default {
    name: 'shorty-item',
    props: {
        note: {
            type: Object,
            require: true
        },
        index: {
            type: Number,
            require: true
        }
    },
    data() {
        return {
           id: this.note.id,
           text: this.note.text,
           editing: this.note.editing,
           important: this.note.important,
           archive: this.note.archive,
           beforeEdit: '',
           currentDate: new Date()
        }
    },
    directives: {
        focus: {
            inserted: function (el) {
            el.focus()
            }
        }
    },
    filters: {
        niceDate(value) {
            return moment(value).format('ll');
        }
    },
    methods: {
        removeItem(index) {
            this.$emit('removedItem', index);
        },

        editItem() {
            this.beforeEdit = this.text;
            this.editing = true;
        },

        doneEdit() {
            this.editing = false;
            this.$emit('finishedEdit', {
                'index': this.index,
                'note': {
                    id: this.id,
                    text: this.text,
                    editing: this.editing,
                    important: this.important,
                    archive: this.archive
                }
            })
        },

        cancelEdit() {
            this.text = this.beforeEdit;
            this.editing = false;
        },

        thisIsImportant() {
            this.important = !this.important;
            this.$emit('importantOrNot', {
                'index': this.index,
                'note': {
                    id:this.id,
                    text: this.text,
                    editing: this.editing,
                    important: this.important,
                    archive: this.archive
                }
            });
        },

        addToArchive() {
            this.archive = !this.archive;
            this.$emit('archiveOrNot', {
                'index': this.index,
                'note': {
                    id:this.id,
                     text: this.text,
                    editing: this.editing,
                    important: this.important,
                    archive: this.archive
                }
            })
        }

    }
}
</script>

<style lang="scss">
    .item {
        background-color: lighten(#2d7461, 15);
        color: #E6E5E3;
        width: 29%;
        height: 15rem;
        margin: 1rem;
        border-radius: 5%;
        display: flex;
        flex-direction: column;
        justify-content: space-between;

        &--active {
            background-color: darken(#B3B20F, 10);
        }

        &--archive {
            background-color: lighten(#F15822, 10);
        }

        &__text {
            display: inline-block;
            font-size: 1.2rem;
            margin-right: .5rem;
            margin-top: 2rem;
            max-width: 80%;
            overflow-wrap: break-word;

            &--edit {
                margin-top: 1.5rem;
                font-size: 1.4rem;
                padding: .5rem;
                background-color: lighten(#2d7461, 45);
                border: 3px solid #AF2024;
                overflow-wrap: break-word;
    

                &:focus {
                    outline: none;
                    
                }
            }
        }

        &__bell {
            display: inline-block;
            color: #B3B20F;
            font-size: 1.5rem;
            margin-top: 1rem;

          

            &--active {
                color: #0033ff;
            }
        }

        &__up {
            display: flex;
            flex-direction: row;
            justify-content: space-between;
            align-items: flex-start;
            margin: 1rem;
            margin-top: 0;  
        }

        &__btn {
           

            &--important, &--archive, &--remove {
                background-color: transparent;
                border: none;
                cursor: pointer;

                &:focus {
                    border: none;
                    outline: none;
                }
            }
        }

        &__down {
            display: flex;
            flex-direction: row;
            justify-content: space-between;
            align-items: flex-end;
            margin: 1rem;
        }

        &__archive, &__remove {
            font-size: 1.5rem;
            padding-left: .3rem;
        }

        &__archive {
            color: #E7DFD5;

            &:hover {
                
                color: lighten( black, 20);
            }
        }

        &__remove {
            color: #AF2024;

            &:hover {
                
                color: #F15822;
            }
            
        }
    }

    .btn__desactive {
        display: none;
    }


</style>