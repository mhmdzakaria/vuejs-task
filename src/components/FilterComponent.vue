<template>
    <div class="container-fluid my-3 ">
       <div class="row filter-row">
            <div class="col-12 col-sm-6 col-md-3 my-2 my-md-0">
                <select @click="getusers" class="form-select">
                   <option value="">روابط الحسابات | خاص الموردين</option>
                   <option v-for="user in users" :key="user.id">
                        {{user.name}}
                    </option>
               </select>
            </div>
            <div class="col-12 col-sm-6 col-md-3  my-2 my-md-0">
                <select class="form-select" aria-label="Default select example" v-model="account_no" @change="getusers">
                    <option value=""> الحساب | mos </option>
                    <option v-for="user in users" :key="user.id">
                        {{user.id}}
                    </option>
                </select>
            </div>
            <div class="col-12 col-sm-6 col-md-3  my-2 my-md-0">
                <Datepicker placeholder="من تاريخ" v-model="fromdate" @update:modelValue="getusers" format="">
                </Datepicker>
            </div>
            <div class="col-12 col-sm-6 col-md-3  my-2 my-md-0">
                <Datepicker placeholder="من تاريخ" v-model="todate" @update:modelValue="getusers" format="">
                </Datepicker>
            </div>
        </div>
        <div class="row serach-row mt-md-4">
            <button class="div filter-btn col-12 col-sm-4 col-md-3  my-2 my-md-0" @click="getusers">
               <i class="fa-solid fa-filter px-2"></i>
                تصفية
            </button>
            <button class="div report-btn  col-12 col-sm-4 col-md-3  my-2 my-md-0" @click="getusers">
               <i class="fa-solid fa-filter px-2"></i>
               تقرير
                مختصر </button>
            <span class="col-12 col-sm-4 col-md-3  my-2 my-md-0 ">
                <button @click="cleardata" class="refresh-btn">
                    <i class="fa-solid fa-arrows-rotate"></i>
                </button>
            </span>
        </div>
        <div class="row invoice-row mr-md-1  mx-sm-2">
            <button @click="print" class="print-btn col-12 col-sm-6 col-md-3  my-2 my-md-0"> طباعة <i
                    class="fa-solid fa-print"></i></button>
        </div>
        <div class="my-md-5 row mr-md-1  mx-sm-2">
            <button class="  col-12 col-sm-6 col-md-3 print-result  my-2 my-md-0 ">
               كشف حساب : رقم الحساب </button>
            <span class="  col-12 col-sm-6 col-md-4 date-span mr-md-2  my-2 my-md-0  mx-sm-2 w-">
                عن الفترة من{{ fromdate }} {{ todate }}إلى
            </span>
        </div>
        <div class="table-responsive my-sm-3 mt-3 my-md-1">
            <table class="table table-bordered">
                <thead>
                    <tr class="table-row">
                        <th colspan="2" class="col-2">الرصيد</th>
                        <th colspan="2" class="col-2">حركة الحساب</th>
                        <th colspan="8" class="col-8">رصيد سابق : 0</th>
                    </tr>
                </thead>
                <tbody>
                    <tr class="table-row">
                        <td colspan="1" class="col-1">مدين</td>
                        <td colspan="1" class="col-1">دائن</td>
                        <td colspan="1" class="col-1">مدين</td>
                        <td colspan="1" class="col-1">دائن</td>
                        <td colspan="" class="col-3">البيان</td>
                        <td colspan="" class="col-3">التاريخ</td>
                        <td colspan="1" class="col-2">رقم المستند</td>
                    </tr>
                    <tr class="">
                        <td colspan="1" class="col-1">0</td>
                        <td colspan="1" class="col-1">11</td>
                        <td colspan="1" class="col-1">0</td>
                        <td colspan="1" class="col-1">11</td>
                        <td colspan="" class="col-3">purchase amount</td>
                        <td colspan="" class="col-3">date</td>
                        <td colspan="1" class="col-2">1 </td>
                    </tr>
                </tbody>
            </table>
        </div>
        <div class="row table-container">
            <div class="col-0 col-md-4"></div>
            <div class="col-12 col-sm-6 col-md-8 col-sm-12">
                <div class="table-responsive">
                    <table class="table table-bordered">
                        <thead>
                            <tr class="table-row">
                                <th colspan="" class="col-2">الباركود</th>
                                <th colspan="" class="col-2"> الصنف</th>
                                <th colspan="" class="col-2">الكمية</th>
                                <th colspan="" class="col-2">السعر</th>
                                <th colspan="" class="col-2">ض ق م</th>
                                <th colspan="" class="col-2">القيمة</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr class="">
                                <td colspan="1" class="col-1">11125425</td>
                                <td colspan="1" class="col-1"></td>
                                <td colspan="1" class="col-1">1</td>
                                <td colspan="1" class="col-1">10</td>
                                <td colspan="1" class="col-1">%10</td>
                                <td colspan="1" class="col-1">10.00</td>
                            </tr>
                            <tr class="">
                                <td colspan="3" class="col-2">اجمالى القيمة </td>
                                <td colspan="3" class="col-2">10 ريال</td>
                            </tr>
                            <tr class="">
                                <td colspan="3" class="col-2">يضاف ضريبة القيمة المضافة</td>
                                <td colspan="3" class="col-1">10 ريال</td>
                            </tr>
                            <tr class="">
                                <td colspan="3" class="col-2">اجمالى الفاتورة </td>
                                <td colspan="3" class="col-1">10 ريال</td>
                            </tr>
                            <tr class="">
                                <td colspan="3" class="col-2">المدفوع </td>
                                <td colspan="3" class="col-1">10 ريال</td>
                            </tr>
                            <tr class="">
                                <td colspan="3" class="col-2">اجمالى القيمة المضافة</td>
                                <td colspan="3" class="col-1">10 ريال</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import Datepicker from '@vuepic/vue-datepicker';
import '@vuepic/vue-datepicker/dist/main.css'
import axios from 'axios'

export default {
    name: 'FilterComponent',
    components: { Datepicker },
    data: () => ({
        fromdate: null,
        todate: null,
        account_no: "",
        supplier_no: "",
        users: "",
        user: ""
    }),
    methods: {
        print() {
            window.print()
        },
        getusers() {
            axios.get('https://jsonplaceholder.typicode.com/users')
                .then((response) => {
                    console.log(response.data)
                    this.users = response.data
                })
        },
        cleardata() {
           this.users = "";
            this.fromdate = null;
            this.todate = null;
       },
    }
}
</script>
<style >
* {
    font-family: 'Tajawal', sans-serif;
}

body {
    direction: rtl;
}

.filter-row {
    align-items: center;
}

.v-input__slot {
    margin-bottom: 0px;
}

.v-text-field__details {
    display: none;
}

.fa-solid,
.fas {
    font-weight: 900;
    font-size: 10px;
    padding: 0 2px;
}

.dp__menu.dp__menu_index.dp__theme_light {
    top: 52px !important;
}

.dp__pointer {
    cursor: pointer;
    font-family: 'Tajawal';
    font-size: inherit;
    color: black !important;
}

input.dp__pointer.dp__input_readonly.dp__input.dp__input_icon_pad.dp__input_reg {
    padding: 5px 35px;
    border-radius: 30px;
    height: 46px;
}

.serach-row {
    display: flex;
    justify-content: center;
}

.serach-row .div {
    width: fit-content;
}

.serach-row button {
    border: 1px solid gray;
    border-radius: 30px;
    padding: 5px 30px;
    margin: 0 10px;
}

.filter-btn {
    background-color: #2287a4;
    color: white;
}

.report-btn {
    background-color: #2aa741;
    color: white;
}

.serach-row span {
    border: 1px solid transparent;
    border-radius: 30px;
    width: auto;
    margin: 0 10px;
    background-color: transparent;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
}

.theme--light.v-text-field>.v-input__control>.v-input__slot:before {
    display: none;
}

.v-application--is-ltr .v-text-field .v-label {
    transform-origin: unset;
    left: unset !important;
}

.col-3 {
    padding: 5px;
}

select.form-select {
    padding: 10px 0px;
    text-align: center;
    border-radius: 30px;
    font-size: 14px;
    height: 46px;
    cursor: pointer;
}

.theme--light.v-input {
    color: rgba(0, 0, 0, 0.87);
    border: 1px solid gray;
    border-radius: 30px;
}

.v-input input {
    padding: 10px 11px;
    max-height: 36px;
    font-size: 14px;
}

.date-span {
    width: fit-content !important;
}

.print-result,
.print-btn {
    width: fit-content !important;
    border-radius: 30px;
}

.refresh-btn {
    border-radius: 50% !important;
    padding: 5px 20px !important;
    border: 1px solid transparent !important;
    height: 40px;
    width: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
}

.v-menu__contente {
    left: 312px !important;
}

@media (max-width: 768px) {
    .serach-row .div {
        width: 30%;
    }
}

@media (max-width: 575.98px) {
    .serach-row .div {
        width: 90%;
        margin: auto;
    }
   .print-result {
        width: 90% !important;
        margin: auto;
    }
   .date-span {
        width: 90% !important;
        margin: auto;
    }
}
</style>