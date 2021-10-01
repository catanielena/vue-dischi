<template>
    <div class="album">
        <div class="album__img">
            <img :src="item.poster" :alt="item.title">
        </div>
        <h4 class="album__title">{{item.title}}</h4>
        <div class="album__info">
            <p>{{item.author}}</p>
            <p>{{item.year}}</p>
        </div>
    </div>  
</template>

<script>
export default {
    name: "Album",
    props: {
        item: Object
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/common';
    .album {
        $this: &;
        height: 20rem;
        flex-direction: column;
        background-color: $mainColor300;
        padding: $gap;
        margin: $gap-sm;
        text-align: center;

        .album__img {
            position: relative;
            overflow: hidden;
            width: 100%;

            img {
                position: absolute;
                left: 0;
                width: 100%;
            }
        }

        .album__img::after {
            content: "";
            display: inline-block;
            padding-bottom: 100%;
        }

        .album__title {
            color: #fff;
            text-transform: uppercase;
            margin: $gap 0;
        }

        .album__info {
            margin: $gap 0;           
            p {
                display: block;
                font-size: 1rem;
                line-height: .4rem;
                color: $grey;
            }
        }
    }
</style>