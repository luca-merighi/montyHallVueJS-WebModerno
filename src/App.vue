<template>
    <div id="app">
        <h1>Problema de Monty Hall</h1>
        <div class="form">
            <div v-if="!started">
                <label for="portsAmount">Quantas Portas?</label>
                <input class="input" type="text" id="portsAmount" size="3" 
                    v-model.number="portsAmount">
            </div>
            <div v-if="!started">
                <label for="selectedPort">Qual porta é premiada?</label>
                <input class="input" type="text" id="selectedPort" size="3" 
                    v-model.number="selectedPort">
            </div>
            <button class="button" v-if="!started" @click="started = true">Iniciar</button>
            <button class="button" v-if="started" @click="started = false">Reiniciar</button>
        </div>
        <div class="doors" v-if="started">
            <div v-for="i in portsAmount" :key="i">
                <Door :hasGift="i === selectedPort" :number="i" />
            </div>
        </div>
    </div>
</template>

<script>
import Door from './components/Door.vue'

export default {
    name: 'App',
    components: { Door },
    data: function () {
        return {
            started: false,
            portsAmount: 3,
            selectedPort: null
        }
    }
}
</script>

<style>
* {
    box-sizing: border-box;
    font-family: 'Montserrat', sans-serif;
}

body {
    color: #182848;
    background: linear-gradient(270deg, #FC354C 10%, #0ABFBC 100% );
}

#app {
    display: flex;
    flex-direction: column;
    align-items: center;
}

#app h1 {
    background: linear-gradient(270deg, #0ABFBC 10%, #FC354C 100%);
    border: 2px solid #F9F9F9;
    border-radius: 15px;
    padding: 20px;
    margin-bottom: 60px;
    box-shadow: 0px 0px 12px rgba(255, 255, 255, 0.8);
}

.form {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    margin-bottom: 40px;
}

.form, .form input, .form button {
    margin-bottom: 10px;
    font-size: 2rem;
}

.doors {
    align-self: stretch;
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
}

.input {
    background: linear-gradient(270deg, #0ABFBC 10%, #fc3598 100%);
    border: 2px solid #F9F9F9;
    border-radius: 15px;
    padding: 5px;
    box-shadow: 0px 0px 12px rgba(255, 255, 255, 0.8);
    color: #182848;
    font-weight: 700;
    text-align: center;
    outline: none;
    margin-left: 10px;
}

.button {
    background: linear-gradient(270deg, #b214da 10%, #fc3598 100%);
    border: 2px solid #F9F9F9;
    border-radius: 15px;
    padding: 15px;
    box-shadow: 0px 0px 12px rgba(255, 255, 255, 0.8);
    color: #182848;
    font-weight: 700;
    outline: none;
}
</style>