<script setup>
    const props = defineProps(['trocarFiltro', 'primeiroNumero', 'segundoNumero', 'resultado'])
</script>
<template>
    <form class="form p-5 rounded-3">
        <div class="row g-3">
            <div class="col">
                <input  @change="props.primeiroNumero" type="number" class="form-control" placeholder="Digite o primeiro número" id="primeiroNumero" required>
            </div>
            <div class="col">
                <input  @change="props.segundoNumero" type="number" class="form-control" placeholder="Digite o segundo número" required>
            </div>
            <div class="col-md-1">
                    <select @change="props.trocarFiltro" class="form-control">
                        <option value="soma">+</option>
                        <option value="subtracao">-</option>
                        <option value="divisao">/</option>
                        <option value="multiplicacao">*</option>
                    </select>
                </div>
        </div>
        <div class="mt-4" v-if="props.resultado !== null">
            <h4 class="result">Resultado: {{ props.resultado }}</h4>
        </div>
    </form>
</template>

<style scoped>
    
    .form {
        background-color: #F0EBE3;
    }
    .result{
        color: #e58497;
    }
</style>
