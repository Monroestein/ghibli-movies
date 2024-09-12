//    がんばれ!  🌻

<template>
    <main>
        <h1>Hi, {{ user }} !</h1>

        <details>
            <summary>Pick a movie:</summary>
            <ul v-for="movie in movies" v-bind:key="movie.id">
                <li>{{movies.title}}</li>
            </ul>
                <!-- <input type="button" value=":D" @click="fetchMovie"> -->
        </details>

        <section class="movie_section" v-if="movies.id != ''">

            <div class="movie_left">
                <img :src="movies.image" alt="">
            </div>

            <div class="movie_right">
                <h1>{{ movies.originalTitle }}</h1>
                <h2>{{ movies.title }}</h2>
                <h5>{{ movies.releaseDate }}</h5>
                <p>{{ movies.description }}</p>
            </div>

        </section>

    </main>
</template>

<script>
export default {
    name: 'body-comp',
    props: {
        user:{
            type: String,
            Required: true
        },

    },
    data: function(){
        return {
            movies:{
                id: "",
                originalTitle: "",
                title: "",
                image: "",
                description: "",
                releaseDate: ""
            }
        }
    },
    // computed: {},
    methods: {
        async fetchMovie(){
            try {

                const response = await fetch("https://ghibliapi.vercel.app/films/");
                const json = await response.json();
                // console.log(json)
                this.addMovie(json)
                
            } catch (error) {
                console.log(error)
            }
        },

        addMovie(movieData){
            this.movies = movieData;
            console.log(movieData)
        }
    },
    // watch: {},
    // components: {},
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    // -- End Lifecycle Methods
}
</script>

<style scoped>
    
details {
    margin: 30px auto 80px auto;
    border: 1px solid #c5e2d9;
    border-radius: 3px;
    padding: 0.5em 0.5em 0;
    max-width: 700px;
}

summary {
    font-weight: bold;
    margin: -0.5em -0.5em 0;
    padding: 0.5em;
}

details[open] {
    padding: 0.5em;
}

details[open] summary {
    /* border-bottom: 1px solid #aaa; */
    margin-bottom: 0.5em;
}
</style>