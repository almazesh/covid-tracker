<template>
    <select @change="onChange()" v-model="selected" class="select">
        <option value="0">Select Country</option>
        <option v-for="country of countries" :value="country.ID" :key="country.ID">{{country.Country}}</option>
    </select>
</template>


<script>
    export default {
        name:'CountrySelect',
        props:['countries'],
        data(){
            return{
                selected:0
            }
        },
        methods:{
            onChange(){
                const country = this.countries.find(item => item.ID === this.selected)

                this.$emit('get-country' , country)
            }
        } 
    }
</script>



<style scoped>
    select{
        width: 100%;
        margin-top: 50px;
        padding: 15px 0;
    }
</style>