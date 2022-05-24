
<template>
    <section>
        <h2>{{title}}</h2>
       <ul>
        <li v-for="(item) in items" :key="item.id">
          id: {{item.id}}<br />
          titolo originale: {{item.original_title ? item.original_title : item.original_name}}<br />
          titolo: {{item.title ? item.title : item.name}}<br />
          lingua: <country-flag :country='language(item)' size='small'/><br />
          voto: {{item.vote_average}}<br />
        </li>
      </ul>
     
    </section>
</template>

<script>
import CountryFlag from 'vue-country-flag'
//import {state, actions} from '../store.js'
export default {
    name: 'GridList',
    components:{CountryFlag},
    props:{
        items: Array,
        loader: Boolean,
        title: String
    },//['items','loader'],
    data(){
        return {
            
        }
    },
    computed: {
        // mysearch(){
        //     return state.search
        // }
    },
    methods:{
        language(film){
            if(film.original_language === 'en'){
                return film.original_language = 'gb'
            }else if(film.original_language === 'ja'){
                return film.original_language = 'jp'
            }else{
                return film.original_language
            }
        }
    }
}
</script>

<style lang="scss">
</style>