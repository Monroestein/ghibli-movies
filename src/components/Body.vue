//    がんばれ!  🌻

<template>
    <main>
        <h1>Hi, {{ user }} !</h1>

        <select @change="showMovie">
                <option value="">Pick movie</option>
                <option v-for="movie in movies" :key="movie.id" :value="movie.id">{{ movie.title }}</option>
        </select>

        <section class="movie_section" v-if="selectedFilm!=null">

            <div class="movie_left">
                <img :src="selectedFilm.image" alt="">
            </div>

            <div class="movie_right">
                <h1>{{ selectedFilm.original_title }}</h1>
                <h2>{{ selectedFilm.title }}</h2>
                <h5>{{ selectedFilm.release_date }}</h5>
                <p>{{ selectedFilm.description }}</p>
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
            movies:[
            //     {
            //     id: '',
            //     originalTitle: '',
            //     title: "",
            //     image: "",
            //     description: "",
            //     releaseDate: ""
            // }
        ],
        selectedFilm: null
        }
    },
    // computed: {},
    methods: {
        async fetchMovie(){
            try {

                const response = await fetch("https://ghibliapi.vercel.app/films/");

                if (!response.ok){
                    if (response.status===404){
                        alert(`Movie not found.`);
                        return;
                    }
                    else {
                        throw new Error(`HTTP Error`+response.status)
                    }
                }

                const json = await response.json();
                console.log(json)
                this.addMovie(json)
                
            } catch (error) {
                console.log(error)
            }
        },

        addMovie(movieData){
            this.movies = movieData;
            console.log(movieData)
        },
        showMovie(event){
            const id = event.target.value
            this.selectedFilm = this.movies.find((movie)=>{
                return movie.id==id
            })
        }
    },
    // watch: {},
    // components: {},
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    created(){
        this.fetchMovie()
    }
    // -- End Lifecycle Methods
}
</script>

<style scoped>

main{
    font-size: .8rem;
}
    
.movie_section{
    margin: 60px auto;
    width: 40%;
    display: flex;
    align-items: stretch;
    text-align: start;
    gap: 60px;
}

.movie_left{
    width: 40%;
}

.movie_left img{
  width: 100%;
}

.movie_right{
    width: 40%;
}

.movie_right h1{
    font-size: 400%;
}



</style>