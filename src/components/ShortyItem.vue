<template>
    
        <div class="item">
            <div class="item__text">{{ text }}</div>
            <i class="fas fa-bell item__bell"></i>
            <span class="item__date">{{ currentDate | niceDate }}</span>
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
        width: 30%;
        height: 15rem;
        margin: 1rem 0;
        border-radius: 5%;

        &__text {
            border: 1px solid pink;
            display: inline-block;
        }

        &__bell {
           
            display: inline-block;
            color: yellow;
            border: 1px solid pink;
        }
    }
</style>