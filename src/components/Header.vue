<template>
    <header class="header">
        <div class="header__logo">
            <img :src='logoImg' alt="spotify_logo">
        </div>
        <div class="filter">
            <label for="genre">Select the genre</label>
            <select name="genre" id="genre" v-model="genreSelected" @change='$emit("selectedGenre", genreSelected)'>
                <option selected disabled>Select the genre</option>
                <option value="">All</option>
                <option :value="item" v-for="(item, i) in genre" :key="i">{{item}}</option>
            </select> 
            <label for="author">Select the author</label>
            <select name="author" id="author" v-model="authorSelected" @change='$emit("selectedAuthor", authorSelected)'>
                <option selected disabled>Select the author</option>
                <option value="">All</option>
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
        author: Array
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
        z-index: 1;
        top: 0;
        width: 100%;
        padding: $padHeaderTB $padHeaderRL;        
        background-color: $mainColor300;
        color: #fff;

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