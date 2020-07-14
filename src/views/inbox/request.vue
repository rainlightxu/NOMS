<template>
  <div class="app-container">
    <div class="app-content">
      <div class="filter-container">
        <el-input
          v-model="listQuery.RequestNo"
          class="filter-item"
          placeholder="RequestNo"
          clearable
          @keydown.enter.native="handleFilter"
        ></el-input>
        <el-select
          v-model="listQuery.Department"
          placeholder="Department"
          class="filter-item"
          clearable
          @change="handleFilter"
        >
          <el-option
            v-for="item in departments"
            :key="item.value"
            :label="item.label"
            :value="item.value"
          ></el-option>
        </el-select>
        <el-button type="primary" class="filter-item">搜索</el-button>
        <div class="filter-container" style="float:right;">
          <!-- <el-button type="primary" icon="el-icon-plus">New Request</el-button> -->
          <el-button type="primary" icon="el-icon-download">Export</el-button>
        </div>
      </div>
      <el-table
        ref="multipleTable"
        :data="tableData"
        tooltip-effect="dark"
        style="width: 100%"
        @selection-change="handleSelectionChange"
        border
      >
        <el-table-column type="selection" width="55"></el-table-column>
        <el-table-column label="Request No">
          <template slot-scope="scope">
            <el-link type="primary">{{ scope.row.RequestNo }}</el-link>
          </template>
        </el-table-column>
        <el-table-column prop="Site" label="Site" show-overflow-tooltip>
          <template slot-scope="scope">
            <el-link type="primary">{{ scope.row.Site }}</el-link>
          </template>
        </el-table-column>
        <el-table-column prop="Department" label="Department"></el-table-column>
        <el-table-column prop="RequestBy" label="Request By">
          <template slot-scope="scope">
            <el-link type="primary">{{ scope.row.RequestBy }}</el-link>
          </template>
        </el-table-column>
        <el-table-column prop="Amount" label="Amount"></el-table-column>
        <el-table-column prop="Description" label="Description"  width="160"></el-table-column>
        <el-table-column prop="Status" label="Status"></el-table-column>
        <el-table-column prop="ApproveDate" label="Approve Date"></el-table-column>
        <el-table-column prop="Range" label="Range"></el-table-column>
        <el-table-column prop="ExpDeliveryDate" label="Expect Delivery Date"  width="160"></el-table-column>
        <el-table-column label="Action" width="300" align="center">
          <template slot-scope="scope">
            <el-tooltip class="item" effect="dark" content="Request Detail" placement="top-start">
              <el-button icon="el-icon-search" type="primary" plain circle size="mini"></el-button>
            </el-tooltip>
            <el-tooltip class="item" effect="dark" content="Reject Request" placement="top-start">
              <el-button icon="el-icon-close" type="danger" plain circle size="mini"></el-button>
            </el-tooltip>
            <el-tooltip class="item" effect="dark" content="Forward" placement="top-start">
              <el-button icon="el-icon-share" type="primary" plain circle size="mini"></el-button>
            </el-tooltip>
            <el-tooltip
              class="item"
              effect="dark"
              content="Upload Attactments"
              placement="top-start"
            >
              <el-button type="info" plain icon="el-icon-upload" circle size="mini"></el-button>
            </el-tooltip>
            <el-tooltip class="item" effect="dark" content="Quotation" placement="top-start">
              <el-button type="success" plain icon="el-icon-s-order" circle size="mini"></el-button>
            </el-tooltip>
            <el-tooltip
              class="item"
              effect="dark"
              content="Contract Management"
              placement="top-start"
            >
              <el-button
                type="info"
                plain
                icon="el-icon-setting"
                circle
                size="mini"
                @click="goAddContract(scope.row)"
              ></el-button>
            </el-tooltip>
          </template>
        </el-table-column>
      </el-table>
      <pagination
        v-show="total>0"
        :total="total"
        :page.sync="listQuery.page"
        :limit.sync="listQuery.limit"
        @pagination="getList"
      />
    </div>
  </div>
</template>

<script>
import Pagination from "@/components/Pagination"; // Secondary package based on el-pagination
import { parseTime } from "@/utils";
export default {
  components: { Pagination },
  data() {
    return {
      total: 5,
      listQuery: {
        Department: "",
        RequestNo: "",
        page: 1,
        limit: 5
      },
      departments: [
        { label: "IT", value: 0 },
        { label: "Logistics", value: 1 },
        { label: "IE facality", value: 2 },
        { label: "PM Seating", value: 3 }
      ],
      tableData: [
        {
          RequestNo: "PR000000343257",
          Site: "Guangdong-FIAT, Guangzhou, China",
          Department: "IT",
          RequestBy: "Zhao, Kaibin",
          Amount: 1000,
          Description: "Budgeted/Forecasted",
          Status: "New",
          ApproveDate: "2020-7-8",
          Range: 1,
          ExpDeliveryDate: "2020-7-21"
        }
      ],
      multipleSelection: []
    };
  },
  methods: {
    getList() {},
    handleFilter() {},
    handleSelectionChange(val) {
      this.multipleSelection = val;
    },
    goAddContract(row) {
      console.log(row);
      const reqNo = row.RequestNo;
      this.$router.push("/inbox/request/" + reqNo);
    }
  }
};
</script>

<style>
</style>