<template>
  <div class="app-container">
    <div class="header">
      <h2>Contract: [ Release N-181-002-20200707 for approval ]</h2>
      <div>
        <el-button v-loading="loading" style="margin-left: 10px;" type="success" @click="handleRelease" >Release</el-button>
        <el-button v-loading="loading" type="warning" @click="handleCancel">Cancel</el-button>
      </div>
    </div>
    <el-row style="background-color:white;border-radius:4px;">
      <el-col :span="8">
        <el-form ref="form" :model="form" label-width="225px" inline>
          <el-card>
            <div slot="header" class="clearfix">
              <span>General</span>
              <!-- <el-button style="float: right; padding: 3px 0" type="text">Recommended Suppliers</el-button> -->
            </div>
            <el-form-item label="Entity" :label-width="formLabelWidth">
              <el-select v-model="form.Entity">
                <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                <el-option label="Shanghai" value="Shanghai"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Contract Number" :label-width="formLabelWidth">
              <el-input v-model="form.ContractNumber" style="width:300px"></el-input>
            </el-form-item>
            <el-form-item label="Contract Spend" :label-width="formLabelWidth">
              <el-input v-model="form.ContractSpend" style="width:300px"></el-input>
            </el-form-item>

            <el-form-item label="Buyer" :label-width="formLabelWidth">
              <el-input v-model="form.Buyer"></el-input>
            </el-form-item>
            <el-form-item label="Description" :label-width="formLabelWidth">
              <el-input type="textarea" v-model="form.explanation" style="width:300px;"></el-input>
            </el-form-item>
          </el-card>
          <el-card>
            <div slot="header" class="clearfix">
              <span>Details</span>
              <!-- <el-button style="float: right; padding: 3px 0" type="text">Recommended Suppliers</el-button> -->
            </div>
            <el-form-item label="Contract Type" :label-width="formLabelWidth">
              <el-select v-model="form.ContractType">
                <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                <el-option label="Shanghai" value="Shanghai"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Sourcing Type" :label-width="formLabelWidth">
              <el-select v-model="form.SourcingType">
                <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                <el-option label="Shanghai" value="Shanghai"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Supplier Name" :label-width="formLabelWidth" >
              <el-input v-model="form.SupplierName" style="width:300px"></el-input>
            </el-form-item>
            <el-form-item label="Commodity" :label-width="formLabelWidth">
              <el-select v-model="form.Commodity">
                <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                <el-option label="Shanghai" value="Shanghai"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Payment Term" :label-width="formLabelWidth">
              <el-select v-model="form.PaymentTerm">
                <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                <el-option label="Shanghai" value="Shanghai"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Agreement Type" :label-width="formLabelWidth">
              <el-select v-model="form.AgreementType">
                <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                <el-option label="Shanghai" value="Shanghai"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Terms & Conditions" :label-width="formLabelWidth">
              <el-select v-model="form.TermsAndConditions">
                <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                <el-option label="Shanghai" value="Shanghai"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Contract Coverage" :label-width="formLabelWidth">
              <el-select v-model="form.ContractCoverage">
                <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                <el-option label="Shanghai" value="Shanghai"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Contract Division" :label-width="formLabelWidth">
              <el-select v-model="form.ContractDivision">
                <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                <el-option label="Shanghai" value="Shanghai"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Start Date" :label-width="formLabelWidth">
              <el-date-picker v-model="form.StartDate" type="date" placeholder="选择日期"></el-date-picker>
            </el-form-item>
            <el-form-item label="Expiration Date" :label-width="formLabelWidth">
              <el-date-picker v-model="form.ExpirationDate" type="date" placeholder="选择日期"></el-date-picker>
            </el-form-item>

            <el-form-item label="SSL" :label-width="formLabelWidth">
              <el-select v-model="form.SSL">
                <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                <el-option label="Shanghai" value="Shanghai"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Rebate" :label-width="formLabelWidth">
              <el-select v-model="form.Rebate">
                <el-option label="Facility" value="Facility"></el-option>
                <el-option label="Engineering" value="Engineering"></el-option>
                <el-option label="Logistics" value="Logistics"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Free Spare Part" :label-width="formLabelWidth">
              <el-select v-model="form.RreeSparePart">
                <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                <el-option label="Shanghai" value="Shanghai"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label=" "  :label-width="formLabelWidth">
              <el-button type="primary" @click="onSubmit">Save</el-button>
              <el-button>Cancel</el-button>
            </el-form-item>
          </el-card>
        </el-form>
      </el-col>
      <el-col :span="16">
        <el-card>
          <div slot="header" class="clearfix">
            <span>Reference Information</span>
            <!-- <el-button style="float: right; padding: 3px 0" type="text">Add new contract</el-button> -->
          </div>
          <el-table :data="tableData" border style="width: 100%">
            <el-table-column prop="BasedPR" label="Based PR"></el-table-column>
            <el-table-column prop="PARNumber" label="PAR Number"></el-table-column>
            <el-table-column prop="PRStatus" label="PR Status"></el-table-column>
            <el-table-column prop="PRCost" label="PR Cost"></el-table-column>
            <el-table-column prop="AllocatdSpend" label="Allocatd Spend"></el-table-column>
            <el-table-column prop="ActiveContractCosts" label="Active Contract Costs Spend"></el-table-column>
            <el-table-column prop="Analusis" label="Analysis"></el-table-column>
            <!-- <el-table-column label="opt">
              <el-button type="primary" plain circle icon="el-icon-edit" size="mini"></el-button>
              <el-button type="danger" plain circle icon="el-icon-delete" size="mini"></el-button>
            </el-table-column>-->
          </el-table>
        </el-card>
        <el-card>
          <div slot="header" class="clearfix">
            <span>Attachments</span>
            <!-- <el-button style="float: right; padding: 3px 0" type="text">Add new item</el-button> -->
          </div>
          <el-upload
            class="upload-demo"
            drag
            action="https://jsonplaceholder.typicode.com/posts/"
            multiple
          >
            <i class="el-icon-upload"></i>
            <div class="el-upload__text">
              将文件拖到此处，或
              <em>点击上传</em>
            </div>
            <!-- <div class="el-upload__tip" slot="tip">只能上传jpg/png文件，且不超过500kb</div> -->
          </el-upload>
        </el-card>
        <el-card>
          <div slot="header" class="clearfix">
            <span>Approval routing</span>
          </div>
          <el-table :data="approvalRouting" border style="width: 100%">
            <el-table-column prop="approver" label="Approver"></el-table-column>
            <el-table-column prop="status" label="Status"></el-table-column>
            <el-table-column prop="comments" label="Comments"></el-table-column>
            <el-table-column label="Opt">
              <el-button icon="el-icon-edit" type="primary" size="mini" plain circle></el-button>
              <el-button icon="el-icon-delete" type="primary" size="mini" plain circle></el-button>
            </el-table-column>
          </el-table>
        </el-card>
      </el-col>
    </el-row>
        <!-- release dialog -->
    <el-dialog title="Release Request" :visible.sync="dialogFormVisible">
      <div>
        <el-card>
          <div slot="header" class="clearfix">
            <span>Approve / Reject</span>
            <!-- <el-button style="float: right; padding: 3px 0" type="text">操作按钮</el-button> -->
          </div>
          <el-form :model="releaseForm">
            <el-form-item label="Contract" :label-width="formLabelWidth">
              <el-input v-model="releaseForm.contractNo" autocomplete="off" style="width:50%"></el-input>
            </el-form-item>
            <el-form-item label="Action" :label-width="formLabelWidth">
              <el-select v-model="releaseForm.action" placeholder="Please select...">
                <el-option label="Approve" value="Approve"></el-option>
                <el-option label="Approve & Inform" value="Approve & Inform"></el-option>
                <el-option label="Inform" value="Inform"></el-option>
                <el-option label="Reject" value="Reject"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Notes" :label-width="formLabelWidth">
              <el-input type="textarea" v-model="releaseForm.notes" style="width:50%"></el-input>
            </el-form-item>
          </el-form>
        </el-card>
      </div>
      <!-- <el-card>
        <div slot="header" class="clearfix">
          <span>Approval routing</span>
        </div>
        <el-table :data="approvalRouting" border style="width: 100%">
          <el-table-column prop="approver" label="approver"></el-table-column>
          <el-table-column prop="status" label="status"></el-table-column>
          <el-table-column prop="comments" label="comments"></el-table-column>
        </el-table>
      </el-card> -->
      <div slot="footer" class="dialog-footer">
        <el-button @click="dialogFormVisible = false">取 消</el-button>
        <el-button type="primary" @click="confirmRelease">确 定</el-button>
      </div>
    </el-dialog>
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
        ContractNumber: "i.e. N-181-004-20200708",
        ContractSpend: undefined,
        Buyer: "Zhao,Kaibin",
        Description: "",
        ContractType: "Normal",
        SourcingType: "O-Outsource",
        SupplierName: "",
        Commodity: "",
        PaymentTerm: "",
        AgreementType: "",
        TermsAndConditions: "",
        ContractCoverage: "",
        ContractDivision: "",
        StartDate: new Date(),
        ExpirationDate: new Date(),
        SSL: "",
        Rebate: "",
        FreeSparePart: ""
      },
      releaseForm: {
        contractNo: "PR000000343261",
        action: "",
        notes: "",
        
      },
      tableData: [
        {
          BasedPR: "PR000000343256",
          PARNumber: "001",
          PRStatus: "PO Processing",
          PRCost: 1000,
          AllocatdSpend: 45,
          ActiveContractCosts: 45,
          Analusis: "138%"
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
      formLabelWidth: "150px"
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
    handleRelease() {
      this.dialogFormVisible = true;
    },
    handleCancel() {
      this.$router.push("/inbox/contract")
    },
    confirmRelease() {
      this.dialogFormVisible = false
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