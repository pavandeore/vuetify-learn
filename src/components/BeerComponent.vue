<template>
    <div>
        <input class="input" type="search" v-model="search" placeholder="search beers"/>
        <div v-for="beer in filteredBeers" :key="beer.id" id="beer-compo" >
            <div id="each-beer">
                <h3><label>Beer No : </label>{{beer.id}} </h3>
                <h3><label>Name : </label>{{beer.name}} </h3>
                <h3><label>Tag : </label>{{beer.tagline}} </h3>
                <h3><label>ABV : </label>{{beer.abv}} </h3>
                <h3><label>First Brewed : </label>{{beer.first_brewed}}</h3>
                <h3><label>Attenuation Level : </label>{{beer.attenuation_level}} </h3>
                <img class="beer-img" :src="beer.image_url" />
            </div>
        </div>    
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'BeerComponent',
    created(){
        this.getBeers()
    },
    data(){
        return{
            Beers : [],
            errorMsg: '',
            search: ''
        }
    },
    methods: {
        async getBeers(){
            const response  = await axios.get('https://api.punkapi.com/v2/beers')
            const data = await response;
            
            this.Beers = data.data; 
        }
    },
    computed: {
        filteredBeers: function(){
            return this.Beers.filter((beer)=>{
                return beer.name.toLowerCase().match(this.search.toLowerCase())
            });
        }
    }
}
</script>

<style scoped>
.input{
    margin:10px;
    position: absolute;
    padding:10px;
    width: 80vw;
    outline: none;
    border:1.5px solid black;
}
#beer-compo{
    width:290px;  
    background-color: darkcyan;
    color: #fff;
    margin:10px;
    margin-top: 60px;
    padding:13px;
}
#each-beer > h3{
    margin-top:15px;
}
#each-beer > h3 > label{
    color: rgb(53, 54, 48);
}
.beer-img{
    height:220px;
    margin-top:15px;
    position: relative;
    left:50%;
    transform: translateX(-50%);
}

</style>