<template>
    <section class="collection wrapper">
        <div class="container-fluid">
            <div class="row row-cols-2 row-cols-md-3 d-flex align-content-center flex-wrap justify-content-center">
                <div class="col" v-for="(item,i) in filterCollection" :key="`album_${i}`">
                    <Album :item="item"/>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
import axios from 'axios';
import Album from './Album.vue';

export default {
    name: "Collection",
    components: {
        Album
    },
    props: {
        selectedGenre: String,
        selectedAuthor: String
    },
    data() {
        return {
            collection: []
        } 
    },
    created() {
        axios
            .get('https://flynn.boolean.careers/exercises/api/array/music')
            .then(e => {
                this.collection = e.data.response;
                // this.$nextTick(() => {
                //     this.$emit("albumData", this.filterCollection)
                // })
            })
    },
    computed: {
        filterCollection() {
            let clone = this.collection.filter((e) => e.genre.includes(this.selectedGenre) && e.author.includes(this.selectedAuthor));
            let genre = [];
            let author = []
            clone.forEach(e => {
                if(genre.includes(e.genre) == false) {
                genre.push(e.genre)
                } 
                if(author.includes(e.author) == false) {
                author.push(e.author)
                }

            });
            this.$emit("albumGenre", genre);
            this.$emit("albumAuthor", author);
            return clone;
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/common';
    .collection {
        margin: auto;
        .container {
            margin: auto;
            height: 100%;
        }
        .row {
            @include media-breakpoint-up(lg) {
                @include row-cols(5);
            }
        }

        .col {      
            min-height: 18rem;
            flex-grow: 1;
            margin-bottom: $gap;
        }
    }
</style>