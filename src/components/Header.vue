<template>
    <header class="header">
        <div class="header__logo">
            <img :src='logoImg' alt="spotify_logo">
        </div>
       <select name="genre" id="genre" v-model="genreSelected" @change='$emit("selected", genreSelected)'>
           <option value="">Select the genre</option>
           <option value="Pop">Pop</option>
           <option value="Rock">Rock</option>
           <option value="Jazz">Jazz</option>
        </select> 
    </header>
</template>

<script>
export default {
    name: "Header",
    props: {
        logoImg: String
    },
    data() {
        return {
            genreSelected: ""
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

    }

</style>