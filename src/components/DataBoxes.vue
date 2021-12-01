<template>
    <div class="containerBox">
        <div class="row">
            <div class="cardCases">
                <h2>Cases</h2>
                <h3>New: {{stats.NewConfirmed}}</h3>
                <h3>Total: {{stats.TotalConfirmed}}</h3>
            </div>
            <div class="cardCases">
                <h2>Deaths</h2>
                <h3>New: {{stats.NewDeaths}}</h3>
                <h3>Total: {{stats.TotalDeaths}}</h3>
            </div>
        </div>
    </div>
</template>


<script>
    export default {
        name:'DataBoxes',
        props:['stats']
    }
</script>


<style scoped>
    .containerBox{
        widows: 80%;
        margin:auto;
    }

    .row{
        display: flex;
        justify-content: space-between;

    }


    .cardCases{
        width: 500px;
        padding: 20px;
        text-align: center;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        height: 180px;
        margin-top: 50px;
        background: blue;
        border-radius: 20px;
        box-shadow: 0 0 5px blue;
        color: white;
    }

    .cardCases h2{
        margin:5px;
        color: white;
    }

    .cardCases h3{
        margin: 5px;
    }
</style>