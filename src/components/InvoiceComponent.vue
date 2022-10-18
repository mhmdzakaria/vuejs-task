<template>
    <div class="container-fluid  mb-5">
   </div>
</template>
<script>
export default {
    name: 'InvoiceComponent',
    methods: {
    }
}
</script>
<style  >
button {
    border: 1px solid grey;
    padding: 5px 30px;
    border-radius: 30px;
    width: 100px;
}

table {
    text-align: start;
}

.table-row {
    background-color: #323eb6;
    color: white;
}

.table-container {
    margin-top: -20px !important;
}

.date-span {
    border: 1px solid grey;
    padding: 5px 30px;
    border-radius: 30px;
}

.print-btn {
    background-color: #2a90af;
    color: white;
    border-radius: 30px;
}

.print-result {
    color: white;
    background-color: #2449ef;
}

.v-menu__contente {
    left: 312px !important;
}

@media (max-width: 768px) {
    .table>:not(caption)>*>* {
        text-align: start;
        font-size: 13px;
    }
}

@media (max-width: 575.98px) {
    .print-btn {
        width: 90%;
        margin: auto;
    }
   .invoice-row {
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }
   .table-container {
        margin-top: -12px;
    }
   .table>:not(caption)>*>* {
        text-align: start;
        font-size: 13px;
    }
   select.form-select {
        font-size: 13px;
    }
}
</style>
