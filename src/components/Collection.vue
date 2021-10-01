<template>
    <p>Collection</p>
</template>

<script>
import axios from 'axios';

export default {
    name: "Collection",
    data() {
        // collection: []
    },
    mounted() {
        axios
            .get('https://flynn.boolean.careers/exercises/api/array/music')
            .then(res => console.log(res.data.response))
            // .then(res => collection = res.data.response)

    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/common';

</style>