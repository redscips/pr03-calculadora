<script setup lang="ts">
// propriedade
const props = defineProps(['num1', 'num2', 'resultado', 'recuperaCampos', 'recuperaCampo2', 'trocaOperacao', 'operacao']);
// 
</script>

<template>
    <!--  -->
    <div class="container pt-5 pe-5 text-center text-white">
        <div class="row">
            <div class="col-12">
                <form action="" class="ps-4 py-5 d-flex">
                    <div class="w-75 d-flex">
                        <input id="id-num1" v-model="props.num1" @change="props.recuperaCampos"
                            class="form-control mb-3 me-3" type="number" placeholder="Digite um número">
                        <select v-model="props.operacao" @change="props.trocaOperacao" name="" id="" class="form-select mb-3 me-3 w-25 rounded-3">
                            <option value="1" selected>+</option>
                            <option value="2">-</option>
                            <option value="3">*</option>
                            <option value="4">/</option>
                        </select>
                        <input id="id-num2" v-model="props.num2" @change="props.recuperaCampo2"
                            class="form-control mb-3" type="number" placeholder="Digite um número">
                    </div>
                    <label id="id-resultado" for="" class="form-label w-25 ms-3 mb-3 text-center">{{ props.resultado
                        }}</label>
                </form>
            </div>
        </div>
    </div>
    <!--  -->
</template>

<style scoped lang="scss">
// importacoes
@use '../sass/variaveis';

// elementos
ul {
    list-style: none;
}

// ids
#id-resultado {
    border: 2px dotted #ccc;
    border-radius: 10px;
    background-color: lighten(variaveis.$corFundo, 30%);
}
</style>