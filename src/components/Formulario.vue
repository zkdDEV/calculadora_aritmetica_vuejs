<script setup>
    const props = defineProps(['getNumber1', 'getNumber2', 'setType'])
</script>

<template>
    <form>
        <div class="row">
            <div class="col-md-5 text-center">
                <input @keyup="props.getNumber1" type="number"
                    placeholder="Digite um número">
            </div>
            <div class="col-md-3">
                <select @change="props.setType" class="text-center p-2">
                    <option value="adicao">+ Adição +</option>
                    <option value="subtracao">- Subtração -</option>
                    <option value="multiplicacao">x Multiplicação x</option>
                    <option value="divisao">/ Divisão /</option>
                </select>
            </div>
            <div class="col-md-4 text-center">
                <input @keyup="props.getNumber2" type="number"
                    placeholder="Digite um número">
            </div>
        </div>
    </form>
</template>

<style scoped>
input {
    border-radius: 10px;
    font-size: 2em;
    border: 5px solid black;
}

select {
    font-size: 32px;
    border-radius: 10px;
    border: 3px solid black;
}
</style>