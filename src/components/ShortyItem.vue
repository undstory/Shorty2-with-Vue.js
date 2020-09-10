<template>
    <div>
        <div>{{ text }} </div>
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
           text: this.note.text
        }
    }
}
</script>

<style lang="scss">

</style>