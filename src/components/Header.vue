<template>
    <header class="header">
        <div class="header__logo">
            <img :src='logoImg' alt="spotify_logo">
        </div>
        <div class="filter">
            <select name="genre" id="genre" v-model="genreSelected" @change='$emit("selectedGenre", genreSelected)'>
                <option value="">Select the genre</option>
                <option :value="item" v-for="(item, i) in genre" :key="i">{{item}}</option>
            </select> 
            <select name="author" id="author" v-model="authorSelected" @change='$emit("selectedAuthor", authorSelected)'>
                <option value="">Select the author</option>
                <option :value="item" v-for="(item, i) in author" :key="i">{{item}}</option>
            </select> 
        </div>
        
    </header>
</template>

<script>
export default {
    name: "Header",
    props: {
        logoImg: String,
        genre: Array,
        author: Array,
        data: Object
    },
    data() {
        return {
            genreSelected: "",
            authorSelected: ""
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/common';

    .header {
        $this: &;
        @include flex--SB-C;
        position: fixed;
        top: 0;
        width: 100%;
        padding: $padHeaderTB $padHeaderRL;        
        background-color: $mainColor300;
        z-index: 1;

        &__logo {
            height: $heightLogo;

            img {
                height: 100%;
            }
        }
        
        select {
            margin: 0 $gap;
        }

    }

</style>