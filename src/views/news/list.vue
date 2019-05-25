<template>
  <el-table :data="tableData" style="width: 100%">
    <el-table-column prop="name" label="景点名称" width="180"></el-table-column>
    <el-table-column prop="content" label="景点内容" width="180"></el-table-column>
    <el-table-column prop="longitude" label="经度"></el-table-column>
    <el-table-column prop="latitude" label="纬度"></el-table-column>
    <el-table-column prop="address" label="地址"></el-table-column>
    <el-table-column prop="tag" label="标签"></el-table-column>
    <el-table-column prop="up" label="点赞数"></el-table-column>
  </el-table>
</template>

<script>
import { fetchList } from "@/api/article";
import Pagination from "@/components/Pagination"; // Secondary package based on el-pagination

export default {
  data() {
    return {
      tableData: [
        {
          name: "桂林·东西巷",
          content: "东西巷是桂林明清时代遗留下的唯一的一片历史街巷",
          longitude: 125.3,
          latitude: 265.6,
          address: "上海市普陀区金沙江路 1518 弄",
          tag: "休闲娱乐",
          up: "258"
        },
        {
          date: "2016-05-04",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1517 弄"
        },
        {
          date: "2016-05-01",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1519 弄"
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1516 弄"
        }
      ]
    };
  }
};
</script>

<style scoped>
.edit-input {
  padding-right: 100px;
}
.cancel-btn {
  position: absolute;
  right: 15px;
  top: 10px;
}
</style>
