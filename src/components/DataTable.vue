<template>
<div>
    {{data in datas}}
    <table class="table" id="datatable">
        <thead class="table-light-bg">
            <th scope="col">Sn</th>
            <th scope="col">First Name</th>
            <th scope="col">Last Name</th>
            <th scope="col">E-mail</th>
            <th scope="col">Address</th>
        </thead>
        <tbody>
            <tr v-for="(item,index) in datas" :key="index">
                <td>{{index+1}}</td>
                <td>{{item.fname}}</td>
                <td>{{item.lname}}</td>
                <td>{{item.eaddress}}</td>
                <td>{{item.add}}</td>
                <td>{{item.checkedVechicle}}</td>
                <td>{{item.location}}</td>
                <td>{{item.payment}}</td>
                <div class="inline-button-block">
                    <button @click="editData(item)">Edit</button>
                    <button @click="deleteData(item)">Delete</button>
                </div>
    </table>

</div>
</template>

<script lang="ts">
import {
    Component,
    Prop,
    Vue,
    Watch
} from "vue-property-decorator";
@Component({

})
export default class DataTable extends Vue {
    //Edit Component Visiblity
    editVisible: boolean;
    @Prop()
    public data!: object;

    datas: any[];
    rowData: object;
    constructor() {
        super()
        this.editVisible = false;
        this.datas = [];
        this.rowData = {};
    }
    //Watches
    @Watch("data")
    onDataChange() {
        this.datas.push(this.data);
    }

}
</script>
