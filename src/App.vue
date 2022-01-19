<template>
  <div>
    <DxDataGrid
      id="gridContainer"
      :data-source="employees"
      key-expr="id"
      :show-borders="true"
    >
      <DxFilterRow
        :visible="showFilterRow"
        :apply-filter="currentFilter"
      />
      <DxHeaderFilter
        :visible="showHeaderFilter"
      />
      <DxSearchPanel
        :visible="true"
        :width="240"
        placeholder="Search..."
      />
      <DxColumn
        :width="100"
        :allow-sorting="false"
        data-field="profile_image"
        cell-template="cellTemplate"
      />
      <DxColumn data-field="employee_name"/>
      <DxColumn data-field="employee_salary" alignment="center"/>
      <DxColumn data-field="employee_age" alignment="center"/>
      <template #cellTemplate="{ data }">
        <img :src="data.value">
      </template>
    </DxDataGrid>
  </div>
</template>
<script>
import {
  DxDataGrid,
  DxColumn,
  DxHeaderFilter,
  DxSearchPanel,
  DxFilterRow,
} from 'devextreme-vue/data-grid';
import axios from 'axios';


export default {
  components: {
    DxDataGrid,
    DxColumn,
    DxHeaderFilter,
    DxSearchPanel,
    DxFilterRow,
  },
  data() {
    return {
      employees: this.fetchEmployee(),
    };
  },
  methods: {
    async fetchEmployee() {
      try {
        const response = await axios.get('https://dummy.restapiexample.com/api/v1/employees');
        this.employees = response.data.data;
      } catch (e) {
        alert('Ошибка')
        }
    }
  },
};
</script>
<style scoped>
#gridContainer {
  height: 600px;
}

/* img {
  height: 100px;
  display: block;
} */
</style>
