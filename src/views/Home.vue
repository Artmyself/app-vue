<template>
<div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <div class="checkoutform">
        <form @submit.prevent="save">
            <h3>Billing address</h3>First Name :
            <input type="text" v-model="fname">
            <br>Last Name :
            <input type="text" v-model="lname">
            <hr>E-mail:
            <input type="email" v-model="eaddress">
            <br>Address :
            <input type="text" v-model="add">
            <hr>
            <input type="checkbox" value="Bike" v-model="checkedVechicle"> I have a bike
            <input type="checkbox" value="Car" v-model="checkedVechicle"> I have a car
            <br>

            <label>Location</label>
            <select v-model="location">
            <option disabled value="">Please select one</option>
            <option :value="'ktm'">Kathmandu</option>
            <option :value="'pkr'">Pokhara</option>
            <option :value="'chi'">Chitwan</option>
            </select>
            <hr>
            <h3>Payment</h3>
            <input type="radio" value="creditcard" v-model="payment"> Credit card
            <input type="radio" value="debitcard" v-model="payment"> Debit card
            <input type="radio" value="paypal" v-model="payment"> PayPal
            <hr>

            <button type="submit">Submit</button>
            <button @click="reset()">Reset</button>

        </form>
    </div>
    <datatable :data="data"></datatable>
</div>
</template>

<script lang="ts">
import {
    Component,
    Prop,
    Vue,
    Watch
} from "vue-property-decorator";
import DataTable from "./DataTable.vue";

@Component({
    components: {
        DataTable
    }
})
export default class Home extends Vue {
    fname: String;
    lname: String;
    eaddress: String;
    add: String;
    checkedVechicle: any;
    location: any;
    payment: String;

    firstname: String;
    lastname: String;
    emailaddress: String;
    address: String;
    checkVechicle: any;
    llocation: any;
    pay: String;

    data: object;
    constructor() {
        super(); // super used to grab the features of the vue
        this.fname = "";
        this.lname = "";
        this.eaddress = "";
        this.add = "";
        this.checkedVechicle = "";
        this.location = "";
        this.payment = "";

        this.firstname = "";
        this.lastname = "";
        this.emailaddress = "";
        this.checkVechicle = "";
        this.address = "";
        this.llocation = "";
        this.pay = "";

        this.data = {};
    }
    submit() {
        if (
            this.fname &&
            this.lname &&
            this.eaddress &&
            this.add &&
            this.checkedVechicle &&
            this.location &&
            this.payment
        ) {
            this.data = {
                firstname: this.fname,
                lastname: this.lname,
                emailaddress: this.eaddress,
                address: this.add,
                checkVechicle: this.checkedVechicle,
                llocation: this.location,
                pay: this.payment
            };
            // alert(this.data);
            this.clear();
        } else {
            alert("Fields cannot be empty");
        }
    }
    clear() {
        this.fname = "";
        this.lname = "";
        this.emailaddress = "";
        this.address = "";
        this.checkedVechicle = "";
        this.location = "";
        this.payment = "";
    }
    reset() {
        this.fname = "";
        this.lname = "";
        this.eaddress = "";
        this.add = "";
        this.checkedVechicle = "";
        this.location = "";
        this.payment = "";
    }
}
</script>
