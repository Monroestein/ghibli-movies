<template>
    <section>
        <div class="title_container">
            <h1>Ghibli Movies</h1>
        </div>
        <div class="input_container">
            <input v-model="firstName" type="text" placeholder="First name">
            <input v-model="lastName" type="text" placeholder="Last name">
            <input @click="saveUser" type="button" value="Send">
        </div>
    </section>
</template>

<script>
export default {
    name: 'welcoming-comp',
    // props: {   },
    data: function () {
        return {
            firstName: "",
            lastName: ""
        }
    },
    computed: {
        user(){
            return this.firstName + " " + this.lastName;
        }
    },
    methods: { 
        saveUser(){
            this.$emit('saveUser', this.user)
        }
    }
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
    margin: auto;
    max-width: 900px;
    min-height: 350px;
    background-image: url('../assets/1354012.png');
    background-size: cover;
    color: transparent;
    background-clip: text;
    background-size: 100%;
    background-repeat: no-repeat;
}

h1{
    margin-block-start: 0em;
    margin-block-end: 0em;
    font-size: 13.125em;
    text-align: center;
    line-height: 160px;
    letter-spacing: -15px;
}

.input_container{
    margin-top: 5rem;
}

input{
    margin: 20px;
    padding: 5px;
}

</style>