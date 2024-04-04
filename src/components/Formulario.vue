<script setup>
    const props = defineProps(['n1','n2','alteraN1', 'alteraN2', 'calculaNumeros', 'operadores','operador','n1Resultado','n2Resultado','operadorResultado','resultado'])
</script>
<template>
    <div class="p-5 bg-light rounded-3">
        <h1 class="mb-3">Calculadora Aritmérica</h1>
        <form>
            <div class="row">
                <div class="col-4">
                    <label for="n1">Informe o primeiro número</label>
                    <input :value="props.n1" @keyup="props.alteraN1" id="n1" type="number" class="form-control" placeholder="">
                </div>
                <div class="col-4">
                    <label for="n2">Informe o segundo número</label>
                    <input :value="props.n2" @keyup="props.alteraN2" id="n2" type="number" class="form-control" placeholder="">
                </div>
                <div class="col-3">
                    <label for="operador">Escolha o operador</label>
                    <select id="operador" class="form-control" @change="props.calculaNumeros">
                        <option class="text-center" :value="operador.nome" v-for="operador in props.operadores">{{operador.simbolo}}</option>
                    </select>
                </div>
            </div>
        </form>
        <p class="mt-5">O resultado da {{props.operador}} de {{props.n1Resultado}} {{props.operadorResultado}} {{props.n2Resultado}} é = <b>{{props.resultado}}</b></p>
    </div>
</template>