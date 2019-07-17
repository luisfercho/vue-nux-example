<template lang="html">
    <div class="container">
        <h1 class="title">Albums</h1>
        <div class="columns is-multiline">
            <AlbumCard :album="album" v-for="album in albums" :key="album.id"></AlbumCard>
        </div>
    </div>
</template>

<script>
    import axios from 'axios';
    import env from '../config/env'
    import AlbumCard from '../components/AlbumCard';
    export default {
        name: "index",
        components:{
            AlbumCard
        },
        data(){
            return {
                albums:[]
            }
        },
        created() {
            axios.get(`${env.endpoint}/albums`)
                .then(res=> {
                    this.albums = res.data;
                })
                .catch(err=>{
                    console.warn(err);
                });
        }
    }
</script>

<style scoped>

</style>