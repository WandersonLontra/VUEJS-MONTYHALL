<template>
    <div id="app">
        <h1>Problema de Monty Hall</h1>

        <div class="form">
            <div v-if="!started">
                <label for="portsAmount">Quantas portas?</label>
                <input type="text" id="portsAmount" size="3" v-model.number="portsAmount">
            </div>
            <div v-if="!started">
                <label for="selectedPort">Qual é a porta premiada?</label>
                <input type="text" size="3" v-model.number="selectedPort">
            </div>
            <button v-if="!started" @click="started = true" >Iniciar</button>
            <button v-if="started" @click="started = false" >Reiniciar</button>
        </div>

        <div class="doors" v-if="started">
            <div v-for="i in portsAmount" :key="i">
                <Door 
                    :number="i"
                    :hasGift="i === selectedPort"
                />
            </div>
        </div>


    </div>
</template>

<script>
    import Door from './components/Door.vue';
    export default {
        name: "App",
        components: { Door },
        data(){
            return{
                started: false,
                portsAmount: 3,
                selectedPort: null,
            }
        }
    };
</script>

<style>
    * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;

        font-family: "Montserrat", sans-serif;
    }
    body {
        color: #fff;
        background: -webkit-linear-gradient(
            to right,
            #00bf8f,
            #001510
        );
        background: linear-gradient(to right, #00bf8f, #001510);
    }
    #app{
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    #app h1{
        border: 1px solid #000;
        background: #0004;
        padding: 20px;
        margin: 60px 0;
    }

    .form{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        margin-bottom: 40px;
    }
    .form, .form input, .form button{
        margin-bottom: 10px;
        font-size: 2rem;
    }

    .doors{
        align-self: stretch;
        display: flex;
        justify-content: space-around;

        flex-wrap: wrap;
    }
</style>