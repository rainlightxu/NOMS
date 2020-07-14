<template>
  <div class="app-container">
    <div class="header">
      <el-page-header @back="goBack" content="Add Contracts">
        <template slot="content">
          Add Contracts [ PR PR000000343256]
        </template>
      </el-page-header>

      <div>
        <!-- <el-button v-loading="loading" style="margin-left: 10px;" type="success">Save</el-button>
        <el-button v-loading="loading" type="warning">Cancel</el-button> -->
      </div>
    </div>
    <el-row style="background-color:white;border-radius:4px;">
      <el-col :span="8">
        <el-card>
          <el-form ref="form" :model="form" :label-width="formLabelWidth">
            <el-form-item label="Entity">
              <el-select v-model="form.Entity">
                <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                <el-option label="Shanghai" value="Shanghai"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Auto Contract Number">
              <el-switch v-model="form.AutoContractNumber"></el-switch>
            </el-form-item>
            <el-form-item label="Contract Number">
              <el-input v-model="form.ContractNumber" style="width:300px"></el-input>
            </el-form-item>
            <el-form-item label="PAR Number">
              <el-input v-model="form.PARNumber" style="width:300px"></el-input>
            </el-form-item>
            <el-form-item label="Contract Type">
              <el-select v-model="form.ContractType">
                <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                <el-option label="Shanghai" value="Shanghai"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Sourcing Type">
              <el-select v-model="form.SourcingType">
                <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                <el-option label="Shanghai" value="Shanghai"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Supplier Name">
              <el-input v-model="form.SupplierName" style="width:300px"></el-input>
            </el-form-item>
            <el-form-item label="Supplier QAD Code">
              <el-input v-model="form.SupplierQADCode" style="width:300px"></el-input>
            </el-form-item>

            <el-form-item label="Contract Spend">
              <el-input v-model="form.ContractSpend" style="width:300px"></el-input>
            </el-form-item>
            <el-form-item label="Commodity">
              <el-select v-model="form.Commodity">
                <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                <el-option label="Shanghai" value="Shanghai"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Payment Term">
              <el-select v-model="form.PaymentTerm">
                <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                <el-option label="Shanghai" value="Shanghai"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Agreement Type">
              <el-select v-model="form.AgreementType">
                <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                <el-option label="Shanghai" value="Shanghai"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Terms & Conditions">
              <el-select v-model="form.TermsAndConditions">
                <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                <el-option label="Shanghai" value="Shanghai"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Contract Coverage">
              <el-select v-model="form.ContractCoverage">
                <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                <el-option label="Shanghai" value="Shanghai"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Contract Division">
              <el-select v-model="form.ContractDivision">
                <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                <el-option label="Shanghai" value="Shanghai"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Start Date">
              <el-date-picker v-model="form.StartDate" type="date" placeholder="选择日期"></el-date-picker>
            </el-form-item>
            <el-form-item label="Expiration Date">
              <el-date-picker v-model="form.ExpirationDate" type="date" placeholder="选择日期"></el-date-picker>
            </el-form-item>
            <el-form-item label="Description">
              <el-input type="textarea" v-model="form.explanation" style="width:300px;"></el-input>
            </el-form-item>

            <el-form-item label="SSL">
              <el-select v-model="form.SSL">
                <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                <el-option label="Shanghai" value="Shanghai"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Rebate">
              <el-select v-model="form.Rebate">
                <el-option label="Facility" value="Facility"></el-option>
                <el-option label="Engineering" value="Engineering"></el-option>
                <el-option label="Logistics" value="Logistics"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Free Spare Part">
              <el-select v-model="form.RreeSparePart">
                <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                <el-option label="Shanghai" value="Shanghai"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Vendor Bindding">
              <el-select v-model="form.Vendor3Bindding">
                <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                <el-option label="Shanghai" value="Shanghai"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Approval Workflow">
              <el-switch v-model="form.ApprovalWorkflow"></el-switch>
            </el-form-item>
            <el-form-item>
              <el-button type="primary" @click="onSubmit">Save</el-button>
              <el-button>Cancel</el-button>
            </el-form-item>
          </el-form>
        </el-card>
      </el-col>
      <el-col :span="16">
        <el-card>
          <div slot="header" class="clearfix">
            <span>Available Contracts of PR000000343256</span>
            <el-button style="float: right; padding: 3px 0" type="text">Add new contract</el-button>
          </div>
          <!-- <el-button style="margin-bottom:5px;">Add new item</el-button> -->
          <el-table :data="tableData" border style="width: 100%">
            <el-table-column prop="ContractNo" label="Contract/PO"></el-table-column>
            <el-table-column prop="Supplier" label="Supplier"></el-table-column>
            <el-table-column prop="SupplierQADCode" label="SupplierQADCode"></el-table-column>
            <el-table-column prop="Status" label="Status"></el-table-column>
            <el-table-column prop="Spend" label="Spend"></el-table-column>
            <el-table-column label="opt">
              <el-button type="primary" plain circle icon="el-icon-edit" size="mini"></el-button>
              <el-button type="danger" plain circle icon="el-icon-delete" size="mini"></el-button>
            </el-table-column>
          </el-table>
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      loading: false,
      activeNames: ["1", "2", "3", "4"],
      form: {
        Entity: "Guangdong-FIAT, Guangzhou, China",
        AutoContractNumber: true,
        ContractNumber: "i.e. N-181-004-20200708",
        PARNumber: "",
        ContractType: "Normal",
        SourcingType: "O-Outsource",
        SupplierName: "",
        SupplierQADCode: "",
        ContractSpend: undefined,
        Commodity: "",
        PaymentTerm: "",
        AgreementType: "",
        TermsAndConditions: "",
        ContractCoverage: "",
        ContractDivision: "",
        StartDate: new Date(),
        ExpirationDate: new Date(),
        Description: "",
        SSL: "",
        Rebate: "",
        FreeSparePart: "",
        Vendor3Bindding: "",
        ApprovalWorkflow: true
      },
      tableData: [
        {
          ContractNo: "N-181-002-20200707",
          Supplier: "test",
          SupplierQADCode: "test",
          Status: "New",
          Spend: 45
        }
      ],
      approvalRouting: [
        {
          approver: "张三",
          status: "processing",
          comments: "pass"
        }
      ],
      dialogFormVisible: false,
      itemForm: {
        description: "",
        specification: "",
        unitMeasure: "",
        category: "",
        costCenter: "",
        accountingCode: "",
        subAccountingCode: "",
        foreAmount: "",
        explanation: "",
        qty: "",
        curreny: "CNY",
        unitPrice: undefined,
        reqDeliveryDate: new Date(),
        comments: ""
      },
      formLabelWidth: "170px"
    };
  },
  methods: {
    handleChange(val) {
      console.log(val);
    },
    onSubmit() {
      console.log("submit!");
    },
    handleAddNewItem() {
      this.dialogFormVisible = true;
    },
    goBack() {
      console.log("go back");
      this.$router.go(-1)
    }
  }
};
</script>

<style lang="scss" scoped>
.app-container {
  .el-form-item {
    margin-bottom: 10px;
  }
  /deep/ .el-collapse-item__content {
    padding-bottom: 0;
  }
  .header {
    padding: 0 15px;
    height: 50px;
    width: 100%;
    background-color: #219ef6;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
}
</style>