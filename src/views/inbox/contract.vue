<template>
  <div class="app-container">
    <div class="app-content">
      <div class="filter-container">
        <el-input
          v-model="listQuery.ContractNo"
          class="filter-item"
          placeholder="Contract"
          clearable
          @keydown.enter.native="handleFilter"
        ></el-input>
        <el-input
          v-model="listQuery.MainPR"
          class="filter-item"
          placeholder="Main PR"
          clearable
          @keydown.enter.native="handleFilter"
        ></el-input>
        <!-- <el-select
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
        </el-select>-->
        <el-button type="primary" class="filter-item">搜索</el-button>
        <div class="filter-container" style="float:right;">
          <!-- <el-button type="primary" icon="el-icon-plus">New Contract</el-button> -->
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
        <el-table-column label="Contract No">
          <template slot-scope="scope">
            <el-link type="primary">{{ scope.row.ContractNo }}</el-link>
          </template>
        </el-table-column>
        <el-table-column prop="MainSite" label="Main Site" show-overflow-tooltip>
          <template slot-scope="scope">
            <el-link type="primary">{{ scope.row.MainSite }}</el-link>
          </template>
        </el-table-column>
        <el-table-column prop="MainPR" label="Main PR">
          <template slot-scope="scope">
            <el-link type="primary">{{ scope.row.MainPR }}</el-link>
          </template>
        </el-table-column>
        <el-table-column prop="IssuedBy" label="Issued By">
          <template slot-scope="scope">
            <el-link type="primary">{{ scope.row.IssuedBy }}</el-link>
          </template>
        </el-table-column>
        <el-table-column prop="Amount" label="Amount"></el-table-column>
        <el-table-column prop="Description" label="Description"></el-table-column>
        <el-table-column prop="Status" label="Status"></el-table-column>
        <el-table-column prop="Current" label="Current">
          <template slot-scope="scope">
            <el-link type="primary">{{ scope.row.Current }}</el-link>
          </template>
        </el-table-column>
        <el-table-column prop="CreatedDate" label="Created Date"></el-table-column>
        <el-table-column label="Action" width="300" align="center">
          <template slot-scope="scope">
            <el-tooltip class="item" effect="dark" content="Contract Detail" placement="top-start">
              <el-button
                icon="el-icon-search"
                type="primary"
                plain
                circle
                size="mini"
                @click="goPreview"
              ></el-button>
            </el-tooltip>
            <el-tooltip class="item" effect="dark" content="Edit Contract" placement="top-start">
              <el-button icon="el-icon-edit" type="primary" plain circle size="mini" @click="goModify"></el-button>
            </el-tooltip>
            <el-tooltip
              class="item"
              effect="dark"
              content="Upload Attactments"
              placement="top-start"
            >
              <el-button type="info" plain icon="el-icon-upload" circle size="mini"></el-button>
            </el-tooltip>
            <el-tooltip class="item" effect="dark" content="Release Contract" placement="top-start">
              <el-button
                type="success"
                plain
                icon="el-icon-check"
                circle
                size="mini"
                @click="goRelease(scope.row)"
              ></el-button>
            </el-tooltip>
            <el-tooltip class="item" effect="dark" content="Print Contract" placement="top-start">
              <el-button type="info" plain icon="el-icon-printer" circle size="mini"></el-button>
            </el-tooltip>
            <el-tooltip class="item" effect="dark" content="Delete Contract" placement="top-start">
              <el-button type="danger" icon="el-icon-delete" circle size="mini"></el-button>
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
        ContractNo: "",
        MainPR: "",
        Department: "",
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
          ContractNo: "N-181-002-20200707",
          MainSite: "Guangdong-FIAT, Guangzhou, China",
          MainPR: "PR000000343256",
          IssuedBy: "Zhao, Kaibin",
          Amount: 1000,
          Description: "Budgeted/Forecasted",
          Status: "New",
          Current: "Liao, Fuwen",
          CreatedDate: "2020-7-7 12:00:00"
        },
        {
          ContractNo: "N-181-002-20200707",
          MainSite: "Guangdong-FIAT, Guangzhou, China",
          MainPR: "PR000000343256",
          IssuedBy: "Zhao, Kaibin",
          Amount: 1000,
          Description: "Budgeted/Forecasted",
          Status: "New",
          Current: "Liao, Fuwen",
          CreatedDate: "2020-7-7 12:00:00"
        },
        {
          ContractNo: "N-181-002-20200707",
          MainSite: "Guangdong-FIAT, Guangzhou, China",
          MainPR: "PR000000343256",
          IssuedBy: "Zhao, Kaibin",
          Amount: 1000,
          Description: "Budgeted/Forecasted",
          Status: "New",
          Current: "Liao, Fuwen",
          CreatedDate: "2020-7-7 12:00:00"
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
    goRelease(row) {
      console.log(row);
      const reqNo = row.ContractNo;
      this.$router.push("./release/" + reqNo);
    },
    goPreview() {
      this.$router.push("/inbox/preview-po");
    },
    goModify() {
      this.$router.push("/inbox/modify");
    }
  }
};
</script>

<style>
</style>