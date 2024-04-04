<script setup>
    import { reactive } from 'vue';
    import Formulario from './components/Formulario.vue'

    const estado = reactive({
        n1: 0,
        n2: 0,
        operador: 'Soma',
        operadores:[
            {
            simbolo:'+',
            nome: 'Soma'
            },
            {
            simbolo:'-',
            nome: 'Subtração'
            },
            {
            simbolo:'x',
            nome: 'Multiplicação'
            },
            {
            simbolo:'÷',
            nome: 'Divisão'
            }
        ],
        resultado:0,
        n1Resultado: 0,
        n2Resultado: 0,
        operadorResultado: '+',
    })

    const getListaOperadores = () => {
        return estado.operadores;
    }

    const calculaNumeros = (value) =>{
        estado.n1Resultado = estado.n1;
        estado.n2Resultado = estado.n2;
        estado.resultado = 0;
        switch(value){
            case 'Soma':
                estado.operadorResultado = '+'
                estado.operador = value;
                estado.resultado = Number(estado.n1Resultado) + Number(estado.n2Resultado);
                console.log(`n1: ${estado.n1Resultado} - n2:${estado.n2Resultado} = resultado:${estado.resultado}`)
                break;
            case 'Subtração':
                estado.operadorResultado = '-'
                estado.operador = value;
                estado.resultado = estado.n1Resultado - estado.n2Resultado;
                break;
            case 'Multiplicação':
                estado.operadorResultado = 'x'
                estado.operador = value;
                estado.resultado = estado.n1Resultado * estado.n2Resultado;
                break;
            case 'Divisão':
                estado.operadorResultado = '÷'
                estado.operador = value;
                let r = 0;
                console.log("Valor do n2: "+estado.n2Resultado.type)
                if(estado.n2Resultado==0){
                    r = 'Não é possível dividir por 0!'
                }else{
                    r = estado.n1Resultado / estado.n2Resultado;
                }
                estado.resultado = r;
                break;
            default:
                estado.resultado =  0;
        }
    }

    function alteraN1(evento){
        estado.n1 = evento.target.value;
        estado.n1Resultado = evento.target.value
        calculaNumeros(estado.operador)
    }
    function alteraN2(evento){
        estado.n2 = evento.target.value;
        estado.n2Resultado = evento.target.value
        calculaNumeros(estado.operador)
    }
</script>

<template>
    <div class="container">
        <Formulario :n1="estado.n1" :n2="estado.n2"  :calculaNumeros="e => calculaNumeros(e.target.value)"
                    :alteraN1="e => alteraN1(e)"  :alteraN2="e => alteraN2(e)"
                    :n1Resultado="estado.n1Resultado" :n2Resultado="estado.n2Resultado"
                    :operador="estado.operador" :operadorResultado="estado.operadorResultado"
                    :operadores="estado.operadores" :resultado="estado.resultado" />
    </div>

</template>

<style scoped>
</style>
