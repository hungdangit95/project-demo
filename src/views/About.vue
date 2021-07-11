<template>
  <DataTable :data="[]" :metadata="metedata">
    <template v-slot="item">
      <template v-if="item.templateName == 'status'">
        <span :style="styleRow_approverd" v-if="item.scope.row.status == 1"
          >Đang hoạt động</span
        >
        <span
          :style="styleRow_waitting"
          v-if="item.scope.row.status == 2"
          style="color: #ffba00"
          >Đăng ký mới</span
        >
        <span :style="styleRow_reject" v-if="item.scope.row.status == 3"
          >Từ chối</span
        >
        <span :style="styleRow_reject" v-if="item.scope.row.status == 4"
          >Tạm dừng</span
        >
      </template>
    </template>
  </DataTable>
</template>

<script>
import DataTable from "../components/index.vue";
export default {
  name: "About",
  data() {
    return {
      metedata: {
        cssClass: "cssClass",
        sort: "createdDate",
        selectModel: "single",
        noResultMessage: "",
        noResultDescription: "Không tìm thấy gì cả",
        noResultIcon: "",
        noResultImage: "",
        noResultNoBorders: true,
        canSelectAll: true,
        columns: [
          {
            name: "Tên",
            description: "Tên",
            fieldName: "name",
            sortable: true,
            order: 1,
            templateName: "name",
            displayType: "text",
            style: "width:180",
            width: 180,
          },
          {
            name: "Địa chỉ",
            description: "address",
            fieldName: "address",
            sortable: true,
            order: 2,
            displayType: "text",
            style: "width:180",
            width: 180,
          },
          {
            name: "Ngày thành lập",
            description: "date",
            fieldName: "date",
            sortable: true,
            order: 2,
            displayType: "datetime",
            style: "width:180",
            width: 180,
          },
          {
            name: "Trạng thái",
            description: "Status",
            fieldName: "status",
            displayType: "template",
            style: "width:180",
            width: 180,
            templateName: 'status'
          },
        ],
      },
    };
  },
  components: {
    DataTable,
  },
};
</script>