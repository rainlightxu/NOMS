<template>
  <div class="app-container">
    <div class="header">
      <h2>Purchase Request: [ Release - PR000000343261 ]</h2>
      <div>
        <el-button
          v-loading="loading"
          style="margin-left: 10px;"
          type="success"
          @click="handleRelease"
        >Release</el-button>
        <el-button v-loading="loading" type="warning" @click="handleCancel">Cancel</el-button>
      </div>
    </div>
    <reqForm></reqForm>

    <!-- release dialog -->
    <el-dialog title="Release Request" :visible.sync="dialogFormVisible">
      <div>
        <el-card>
          <div slot="header" class="clearfix">
            <span>Approve / Reject</span>
            <!-- <el-button style="float: right; padding: 3px 0" type="text">操作按钮</el-button> -->
          </div>
          <el-form :model="releaseForm">
            <el-form-item label="PR Number" :label-width="formLabelWidth">
              <el-input v-model="releaseForm.prNo" autocomplete="off" style="width:50%"></el-input>
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
      <el-card>
        <div slot="header" class="clearfix">
          <span>Approval routing</span>
          <!-- <el-button style="float: right; padding: 3px 0" type="text">操作按钮</el-button> -->
        </div>
        <el-table :data="approvalRouting" border style="width: 100%">
          <el-table-column prop="approver" label="Approver"></el-table-column>
          <el-table-column prop="status" label="Status"></el-table-column>
          <el-table-column prop="comments" label="Comments"></el-table-column>
        </el-table>
      </el-card>
      <div slot="footer" class="dialog-footer">
        <el-button @click="dialogFormVisible = false">取 消</el-button>
        <el-button type="primary" @click="confirmRelease">确 定</el-button>
      </div>
    </el-dialog>
  </div>
</template>

<script>
import ReqForm from "./components/reqForm";
export default {
  components: { ReqForm },
  data() {
    return {
      loading: false,
      activeNames: ["1", "2", "3", "4"],
      form: {
        name: "Zhao,Kaibin",
        division: "China",
        site: "Guangdong-FIAT",
        department: "IT",
        costCenter: "5400",
        program: "",
        type: "none",
        budFore: false,
        explanation: "test",
        description: "test",
        singleSource: false,
        supplierA: "",
        supplierB: "",
        supplierC: "",
        supplierD: ""
      },
      tableData: [
        {
          description: "项目1",
          specification: "PR001",
          foreAmount: "1000",
          explanation: "",
          uom: "box",
          qty: 23,
          curreny: "CNY",
          price: 100,
          subTotal: 200,
          reqDelivery: "2020-7-7",
          accounting: "",
          comments: ""
        },
        {
          description: "项目1",
          specification: "PR001",
          foreAmount: "1000",
          explanation: "",
          uom: "box",
          qty: 23,
          curreny: "CNY",
          price: 100,
          subTotal: 200,
          reqDelivery: "2020-7-7",
          accounting: "",
          comments: ""
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
      releaseForm: {
        prNo: "PR000000343261",
        action: "",
        notes: "",
        date1: "",
        date2: "",
        delivery: false,
        type: [],
        resource: "",
        desc: ""
      },
      formLabelWidth: "120px",
      approvalRouting: [
        {
          approver: "张三",
          status: "processing",
          comments: "pass"
        }
      ]
    };
  },
  methods: {
    handleChange(val) {
      console.log(val);
    },
    onSubmit() {
      console.log("submit!");
    },
    handleRelease() {
      this.dialogFormVisible = true;
    },
    handleCancel() {
      this.$router.push("/request/list");
    },
    confirmRelease() {
      this.$router.push("/request/list");
      this.dialogFormVisible = false;
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