<template>
    <div>
        <p v-show="address">Rua: {{ address }}</p>
        <p v-show="city">Cidade: {{ city }}</p>
        <p v-show="state">Estado: {{ state }}</p>
        <p v-show="district">Logradouro: {{ district }}</p>
    </div>
</template>
<script>
export default {
    name: 'CepInformation',
    props: {
        state: String,
        city: String,
        district: String,
        address: String
    }
}
</script>

<style scoped>
    div {
        box-shadow: -5px -5px 9px #ffffff73, 5px 5px 7px #5e687949;
        border-radius: 10px;
        padding: 20px;
        color: #222;
        font-weight: bold;
    }
</style>