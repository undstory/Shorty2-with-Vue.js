<template>
    
        <div class="item">
            <div class="item__up">
                <div class="item__text">{{ text }}</div>
                <button class="item__btn--important"><i class="fas fa-bell item__bell"></i></button>
            </div>
            <div class="item__down">
                 <span class="item__date">{{ currentDate | niceDate }}</span>
                 <div class="item__btns">
                     <button class="item__btn--archive"><i class="fas fa-archive"></i></button>
                     <button class="item__btn--remove"><i class="fas fa-trash"></i></button>
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
    }
}
</script>

<style lang="scss">
    .item {
        background-color: #365A66;
        color: #C3D6DC;
        border: 1px solid red;
        width: 29%;
        height: 15rem;
        margin: 1rem;
        border-radius: 5%;
        display: flex;
        flex-direction: column;
        justify-content: space-between;

        &__text {
            border: 1px solid pink;
            display: inline-block;
        }

        &__bell {
           
            display: inline-block;
            color: yellow;
            border: 1px solid pink; 
        }

        &__up {
            display: flex;
            flex-direction: row;
            justify-content: space-between;
        }

        &__down {
            display: flex;
            flex-direction: row;
            justify-content: space-between;
        }
    }
</style>