<template>
    <div id="CepForm">
        <form @submit="searchCep">
            <p>Enter your zip code without special characters</p>
            <input type="text" name="cep" id="cep" v-model="cep" maxlength="8">
            <button class="pushable">
                <span class="front">
                    Search
                </span>
            </button>
        </form>
        <CepInformation :address="address" :state="state" :district="district" :city="city"/>
    </div>
</template>

<script>
import CepInformation from './CepInformation.vue';

export default {
    name: "CepForm",
    data() {
        return {
            cep: null,
            state: null,
            city: null,
            district: null,
            address: null
        };
    },
    methods: {
        async searchCep(e) {
            e.preventDefault()
            var re = /^([\d]{2})\.*([\d]{3})-*([\d]{3})/; // Pode usar ? no lugar do *
            
            if(re.test(this.cep)){
                const req = await fetch(`https://ws.apicep.com/cep.json?code=${this.cep}`);
                const data = await req.json();
                this.state = data.state;
                this.city = data.city;
                this.district = data.district;
                this.address = data.address;
            }else{
                alert("CEP inválido!");
            }
            

            
        }
    },
    components: { CepInformation }
}
</script>

<style scoped>
    #CepForm {
        max-width: 500px;
        margin: 0 auto;
        padding: 100px 30px;
    }

    p {
        text-align: center;

    }

    input {
        width: 90%;
        display: block;
        margin: 10px auto;
        outline: none;
        text-align: center;
        padding: 10px;
        border: none;
        box-shadow: -5px -5px 9px #ffffff73, 5px 5px 7px #5e687949;
        border-radius: 10px;
        font-size: 1.25rem;
    }

    .pushable {
        background: rgb(131, 130, 130);
        border-radius: 12px;
        border: none;
        padding: 0;
        cursor: pointer;
        outline-offset: 4px;
        display: block;
        margin: 20px auto;
    }
    .front {
        display: block;
        padding: 8px 35px;
        border-radius: 12px;
        font-size: 1.15rem;
        background: rgba(161, 161, 161);
        color: white;
        transform: translateY(-6px);
    }

    .pushable:active .front {
        transform: translateY(-2px);
    }

</style>