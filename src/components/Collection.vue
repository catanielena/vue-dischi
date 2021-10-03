<template>
    <section class="collection wrapper">
        <div class="container-fluid">
            <div class="row row-cols-2 row-cols-md-3 d-flex align-content-center flex-wrap justify-content-center">
                <div class="col" v-for="(item,i) in collection" :key="`album_${i}`">
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
    data() {
        return {
            collection: null
        } 
    },
    mounted() {
        axios
            .get('https://flynn.boolean.careers/exercises/api/array/music')
            .then(e => this.collection = e.data.response);
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
            margin-bottom: $gap;
        }
    }
</style>