<template >
  <h2>chan that</h2>
  <el-table
    border
    style="width: 100%"
    :data="tableData"
    class="table-list-partner"
    :row-style="tableRowStyle"
    :header-cell-style="tableHeaderColor"
  >
    <template v-if="metadata.canSelectAll == true">
      <el-table-column type="selection" style="width: 50%" align="center" />
    </template>
    <template v-for="(column, index) in metadata.columns">
     <template v-if="column.displayType == 'template'">
        <el-table-column
          :key="index"
          v-bind="column"
          :prop="column.fieldName"
          :label="column.name"
          :style="column.style"
          :width="column.width"
        >
          <template v-slot="scope">
            <slot
              v-bind="{
                scope: scope,
                templateName: column.templateName,
              }"
            ></slot>
          </template>
        </el-table-column>
      </template>
      <template v-if="column.displayType == 'datetime'">
        <el-table-column
          :key="index"
          v-bind="column"
          :prop="column.fieldName"
          :label="column.fieldName"
          :style="column.style"
          :width="column.width"
        >
          <template v-slot="scope">
            <span>{{ scope.row[column.fieldName] }}</span>
          </template>
        </el-table-column>
      </template>
      <template v-if="column.displayType == 'text'">
        <el-table-column
          :key="index"
          v-bind="column"
          :prop="column.fieldName"
          :label="column.fieldName"
          :style="column.style"
          :width="column.width"
        >
        </el-table-column>
      </template>
    </template>
  </el-table>
</template>

<script>
export default {
  name: "data-table",
  data() {
    return {
      tableData: [
        {
          date: "2016-05-03",
          name: "Tom",
          address: "No. 189, Grove St, Los Angeles",
          status: 1
        },
        {
          date: "2016-05-02",
          name: "Tom",
          address: "No. 189, Grove St, Los Angeles",
          status: 2
        },
        {
          date: "2016-05-04",
          name: "Tom",
          address: "No. 189, Grove St, Los Angeles",
          status: 3
        },
        {
          date: "2016-05-01",
          name: "Tom",
          address: "No. 189, Grove St, Los Angeles",
          status:4
        },
      ],
    };
  },
  props: {
    data: Array,
    metadata: Object,
  },
  methods: {
    tableRowStyle() {
      return "font-family: monospace;font-size: 14px;";
    },
    tableHeaderColor({ rowIndex }) {
      if (rowIndex === 0) {
        return "font-size: 12px;";
      }
    },
  },
};
</script>
