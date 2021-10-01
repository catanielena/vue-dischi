<template>
    <header class="header">
        <div class="header__logo">
            <img :src='logoImg' alt="spotify_logo">
        </div>
    </header>
</template>

<script>
export default {
    name: "Header",
    props: {
        logoImg: String
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/common';

    .header {
        $this: &;
        position: fixed;
        top: 0;
        width: 100%;
        padding: .7rem 1.2rem;        
        background-color: $mainColor300;

        &__logo {
            height: 2.75rem;

            img {
                height: 100%;
            }
        }

    }

</style>