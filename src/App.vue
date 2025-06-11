<script setup lang="ts">
// importacoes
import { reactive, type ObjectEmitsOptions } from 'vue'
// componentes
import Cabecalho from './componentes/Cabecalho.vue';
import Corpo from './componentes/Corpo.vue';
import Roda from './componentes/Roda.vue';
// tipos
import type { objeto } from '@/ts/tipos';

// reativos
let reativos : objeto = reactive({
  num1: 0,
  num2: 0,
  resultado: 0,
  opcaoOp: 1,
});

// funcoes
function efetuaCalculo(): number {
  // var retorno
  let numeroRetorno: number = 0;
  try {
    // tratamentos
    if (isNaN(reativos.num1)) reativos.num1 = 0;
    if (isNaN(reativos.num2)) reativos.num2 = 0;
    console.log(reativos.opcaoOp);
    // efetua calculo
    switch (reativos.opcaoOp) {
      case 2 :
        numeroRetorno = reativos.num1 - reativos.num2;
        break;
      case 3 :
        numeroRetorno = reativos.num1 * reativos.num2;
        break;
      case 4 :
        numeroRetorno = reativos.num1 / reativos.num2;
        break;
      default:
        numeroRetorno = reativos.num1 + reativos.num2;
    }
    // retorna resultado
    reativos.resultado = numeroRetorno;
  } catch (error) {
    console.log(error);
  } finally {
    return numeroRetorno;
  }
}

function trocaOperacao(e: any): void {
  try {
    // troca operacao
    reativos.opcaoOp = parseInt(e.target.value);
     // efetua calculo
     efetuaCalculo();
  } catch (error) {
    console.log(error);
  }
}

function recuperaCampo1(e: any): void {
  try {
    // verifica nome
    reativos.num1 = parseFloat(e.target.value);
    // efetua calculo
    efetuaCalculo();
  } catch (error) {
    console.log(error);
  }
}

function recuperaCampo2(e: any): void {
  try {
    // verifica nome
    reativos.num2 = parseFloat(e.target.value);
    // efetua calculo
    efetuaCalculo();
  } catch (error) {
    console.log(error);
  }
}
// 
</script>

<template>
  <!--  -->
  <header>
    <Cabecalho></Cabecalho>
  </header>
  <main>
    <Corpo :num1="reativos.num1" :num2="reativos.num2" :resultado="reativos.resultado" :recupera-campos="recuperaCampo1"
      :recupera-campo2="recuperaCampo2" :troca-operacao="trocaOperacao" :operacao="reativos.opcaoOp"></Corpo>
  </main>
  <footer>
    <Roda></Roda>
  </footer>
  <!--  -->
</template>

<style scoped lang="scss">
// importacao
@use './sass/variaveis';

// elementos
header {
  background-color: lighten(variaveis.$corFundo, 20%);
}

main {
  // background-color: blue;
  // faz com que o main ocupe todo espaco disponivel
  flex-grow: 1;
}

footer {
  background-color: lighten(variaveis.$corFundo, 10%);
}

/*  */
</style>
