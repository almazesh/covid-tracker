<template>
    <div class="container">
        <h2>{{text}}</h2>
        <div>
            {{timestamp}}
        </div>
    </div>
</template>


<script>
    import moment from 'moment'
    export default{
        name:"DataTitle",
        props:['text' , 'dataDate'],
        computed:{
            timestamp: function(){
                return moment(this.dataDate).format('MMMM Do YYYY, h:mm:ss a')
            }
        }
    }
</script>

<style scoped>
    .container{
        text-align: center;
        margin-top: 50px;
    }
</style>