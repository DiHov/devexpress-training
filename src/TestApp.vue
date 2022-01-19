<template>
    <DxDataGrid
    :columns="columns"
    :show-borders="true"
    data-source="https://dummy.restapiexample.com/api/v1/employees"
    />
</template>

<script>
import DxDataGrid from 'devextreme-vue/data-grid';

export default {
    components: {
        DxDataGrid,
    },
    data() {
        return {
           columns: ['employee_name', 'employee_salary', 'employee_age'],
        }
    },
}
</script>

<style >

</style>