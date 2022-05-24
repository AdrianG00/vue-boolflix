<template>
    <div>
      <input type="text" v-model="search" @keyup.enter="$emit('performSearch',search)">
      <button @click="cerca">Cerca</button>
    </div>
</template>

<script>
//import state from '../store.js'
export default {
    name: 'SearchBar',
    data(){
        return {
           search:'' 
        }
    },
    computed:{
        // mysearch(){
        //     return state.search
        // }
    },
    methods:{
        cerca(){
            this.$emit('performSearch',this.search)
            this.search = ''
        }
    }
}
</script>

<style lang="scss">

</style>