<template>
    
        <div class="item">
            <div class="item__up">
                <div class="item__text">{{ text }}</div>
                <button class="item__btn--important"><i class="fas fa-bell item__bell"></i></button>
            </div>
            <div class="item__down">
                 <span class="item__date">{{ currentDate | niceDate }}</span>
                 <div class="item__btns">
                     <button class="item__btn--archive"><i class="fas fa-plus-circle item__archive"></i></i></button>
                     <button class="item__btn--remove" @click="removeItem(index)"><i class="fas fa-trash item__remove"></i></button>
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
           text: this.note.text,
           currentDate: new Date()
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
        }
    }
}
</script>

<style lang="scss">
    .item {
        background-color: #2d7461;
        color: #E6E5E3;
        width: 29%;
        height: 15rem;
        margin: 1rem;
        border-radius: 5%;
        display: flex;
        flex-direction: column;
        justify-content: space-between;

        &__text {
            display: inline-block;
            font-size: 1.2rem;
            margin-right: .5rem;
            margin-top: 2rem;
        }

        &__bell {
            display: inline-block;
            color: #B3B20F;
            font-size: 1.5rem;
            margin-top: 1rem;

            &:hover {
                color: #F04F33;
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
                
                color: #D76B8B;
            }
        }

        &__remove {
            color: #AF2024;

            &:hover {
                
                color: #F15822;
            }
            
        }
    }


</style>