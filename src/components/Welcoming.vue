<template>
    <section>
        <div class="title_container">
            <h1>Ghibli<br>Movies</h1>
        </div>
        <input type="text" placeholder="Please enter your name">
        <input type="button" value="Send">
    </section>
</template>

<script>
export default {
    name: 'welcoming-comp',
    // props: {},
    data: function () {
        return {}
    },
    // computed: {},
    //methods: {}
    // watch: {},
    // components: {},
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    // -- End Lifecycle Methods
}
</script>

<style scoped>

.title_container{
    width: 80%;
    margin: auto;
}

h1{
    font-size: 210px;
    line-height: 160px;
    letter-spacing: -15px;
    background-image: url('../assets/1354012.png');
    background-size: cover;
    color: transparent;
    background-clip: text;
    background-size: 100%;
    background-repeat: no-repeat;
}

input{
    margin: 20px;
    padding: 5px;
}

</style>