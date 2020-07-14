<template>
  <div>
    <!-- <div class="header">
      <h2>Purchase Request: [ New ]</h2>
      <div>
        <el-button
          v-loading="loading"
          style="margin-left: 10px;"
          type="success"
          @click="submitRequest"
        >Save</el-button>
        <el-button v-loading="loading" type="warning">Cancel</el-button>
      </div>
    </div>-->
    <el-row :gutter="8" style="background-color:white;border-radius:4px;">
      <el-col :span="8">
        <el-card>
          <el-form ref="form" :model="form" label-width="225px">
            <el-collapse v-model="activeNames" @change="handleChange">
              <el-collapse-item name="1">
                <template slot="title">
                  <span>Request by</span>
                </template>

                <el-form-item label="Name">
                  <el-input v-model="form.name" style="width:300px"></el-input>
                </el-form-item>
                <el-form-item label="Division">
                  <el-input v-model="form.division" style="width:300px"></el-input>
                </el-form-item>
                <el-form-item label="Site">
                  <el-select v-model="form.site">
                    <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                    <el-option label="Shanghai" value="Shanghai"></el-option>
                  </el-select>
                </el-form-item>
                <el-form-item label="Department">
                  <el-input v-model="form.department" style="width:300px"></el-input>
                </el-form-item>
                <el-form-item label="Cost Center">
                  <el-input v-model="form.costCenter" style="width:300px"></el-input>
                </el-form-item>
              </el-collapse-item>
              <el-collapse-item title="PAR Number & Program" name="2">
                <el-form-item label="PAR Number & Program">
                  <el-select v-model="form.program">
                    <el-option label="Guangdong-FIAT" value="Guangdong-FIAT"></el-option>
                    <el-option label="Shanghai" value="Shanghai"></el-option>
                  </el-select>
                </el-form-item>
              </el-collapse-item>
              <el-collapse-item title="Facility/Engineering/Logistics" name="3">
                <el-form-item label="Facility/Engineering/Logistics">
                  <el-select v-model="form.type">
                    <el-option label="Facility" value="Facility"></el-option>
                    <el-option label="Engineering" value="Engineering"></el-option>
                    <el-option label="Logistics" value="Logistics"></el-option>
                  </el-select>
                </el-form-item>
              </el-collapse-item>
              <el-collapse-item title="Description" name="4">
                <el-form-item label="Budgeted/Forecasted">
                  <el-switch v-model="form.budFore"></el-switch>
                </el-form-item>
                <el-form-item label="Explanation">
                  <el-input type="textarea" v-model="form.explanation" style="width:300px;"></el-input>
                </el-form-item>
                <el-form-item label="Description">
                  <el-input type="textarea" v-model="form.description" style="width:300px;"></el-input>
                </el-form-item>
                <el-form-item label="Single Source">
                  <el-switch v-model="form.singleSource"></el-switch>
                </el-form-item>
              </el-collapse-item>
            </el-collapse>
            <!-- <el-form-item>
              <el-button type="primary" @click="onSubmit">立即创建</el-button>
              <el-button>取消</el-button>
            </el-form-item>-->
          </el-form>
        </el-card>
      </el-col>
      <el-col :span="16">
        <el-row>
          <el-card>
            <div slot="header" class="clearfix">
              <span>Recommended Suppliers</span>
              <!-- <el-button style="float: right; padding: 3px 0" type="text">Recommended Suppliers</el-button> -->
            </div>
            <div style="display:flex;justify-content:space-around;align-items:center;">
              <label>Supplier A</label>
              <el-select v-model="form.supplierA">
                <el-option label="Facility" value="Facility"></el-option>
                <el-option label="Engineering" value="Engineering"></el-option>
                <el-option label="Logistics" value="Logistics"></el-option>
              </el-select>
              <label>Supplier B</label>
              <el-select v-model="form.supplierB">
                <el-option label="Facility" value="Facility"></el-option>
                <el-option label="Engineering" value="Engineering"></el-option>
                <el-option label="Logistics" value="Logistics"></el-option>
              </el-select>
              <label>Supplier C</label>
              <el-select v-model="form.supplierC">
                <el-option label="Facility" value="Facility"></el-option>
                <el-option label="Engineering" value="Engineering"></el-option>
                <el-option label="Logistics" value="Logistics"></el-option>
              </el-select>
              <label>Supplier D</label>
              <el-select v-model="form.supplierD">
                <el-option label="Facility" value="Facility"></el-option>
                <el-option label="Engineering" value="Engineering"></el-option>
                <el-option label="Logistics" value="Logistics"></el-option>
              </el-select>
            </div>
          </el-card>
        </el-row>
        <el-row>
          <el-card>
            <div slot="header" class="clearfix">
              <span>Items</span>
              <el-button
                style="float: right; padding: 3px 0"
                type="text"
                @click="handleAddNewItem"
              >Add new item</el-button>
            </div>
            <!-- <el-button style="margin-bottom:5px;">Add new item</el-button> -->
            <el-table :data="tableData" border style="width: 100%">
              <el-table-column prop="description" label="Description"></el-table-column>
              <el-table-column prop="specification" label="Specification"></el-table-column>
              <el-table-column prop="foreAmount" label="Comparable Actual/Forecast Amount"></el-table-column>
              <el-table-column prop="explanation" label="Explanation"></el-table-column>
              <!-- <el-table-column prop="uom" label="uom"></el-table-column> -->
              <el-table-column prop="qty" label="Qty"></el-table-column>
              <el-table-column prop="curreny" label="Curreny"></el-table-column>
              <el-table-column prop="price" label="Price"></el-table-column>
              <el-table-column prop="subTotal" label="SubTotal"></el-table-column>
              <!-- <el-table-column prop="reqDelivery" label="Request Delivery"></el-table-column>
            <el-table-column prop="accounting" label="accounting"></el-table-column>
              <el-table-column prop="comments" label="comments"></el-table-column>-->
              <el-table-column label="Opt">
                <el-button type="primary" plain circle icon="el-icon-edit" size="mini"></el-button>
                <el-button type="danger" plain circle icon="el-icon-delete" size="mini"></el-button>
              </el-table-column>
            </el-table>
          </el-card>
        </el-row>
        <el-row>
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
        </el-row>
        <el-row>
          <el-card>
            <div slot="header" class="clearfix">
              <span>Approval routing</span>
              <el-button style="float: right; padding: 3px 0" type="text">Add new approver</el-button>
            </div>
            <!-- <el-button style="margin-bottom:5px;">Add new approver</el-button> -->

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
        </el-row>
      </el-col>
    </el-row>
    <el-dialog title="New Item" :visible.sync="dialogFormVisible">
      <el-form :model="itemForm">
        <el-form-item label="Description" :label-width="formLabelWidth">
          <el-input v-model="itemForm.description" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="Specification" :label-width="formLabelWidth">
          <el-input v-model="itemForm.specification" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="Unit Measure" :label-width="formLabelWidth">
          <el-select v-model="itemForm.unitMeasure">
            <el-option label="区域一" value="shanghai"></el-option>
            <el-option label="区域二" value="beijing"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="Category" :label-width="formLabelWidth">
          <el-select v-model="itemForm.category">
            <el-option label="区域一" value="shanghai"></el-option>
            <el-option label="区域二" value="beijing"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="Cost Center" :label-width="formLabelWidth">
          <el-select v-model="itemForm.costCenter">
            <el-option label="区域一" value="shanghai"></el-option>
            <el-option label="区域二" value="beijing"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="Accounting Code" :label-width="formLabelWidth">
          <el-select v-model="itemForm.accountingCode">
            <el-option label="区域一" value="shanghai"></el-option>
            <el-option label="区域二" value="beijing"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="Sub Accounting Code" :label-width="formLabelWidth">
          <el-select v-model="itemForm.subAccountingCode">
            <el-option label="区域一" value="shanghai"></el-option>
            <el-option label="区域二" value="beijing"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="Comparable Actual/Forecast Amount" :label-width="formLabelWidth">
          <el-select v-model="itemForm.foreAmount">
            <el-option label="区域一" value="shanghai"></el-option>
            <el-option label="区域二" value="beijing"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="Explanation" :label-width="formLabelWidth">
          <el-input type="textarea" v-model="itemForm.explanation" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="Qty" :label-width="formLabelWidth">
          <el-input v-model="itemForm.qty" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="Curreny" :label-width="formLabelWidth">
          <el-select v-model="itemForm.curreny">
            <el-option label="区域一" value="shanghai"></el-option>
            <el-option label="区域二" value="beijing"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="Unit Price" :label-width="formLabelWidth">
          <el-input v-model="itemForm.unitPrice" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="Request Delivery Date" :label-width="formLabelWidth">
          <el-date-picker v-model="itemForm.reqDeliveryDate" type="date" placeholder="选择日期"></el-date-picker>
        </el-form-item>
        <el-form-item label="Comments" :label-width="formLabelWidth">
          <el-input v-model="itemForm.comments" type="textarea" autocomplete="off"></el-input>
        </el-form-item>
      </el-form>
      <div slot="footer" class="dialog-footer">
        <el-button @click="dialogFormVisible = false">取 消</el-button>
        <el-button type="primary" @click="dialogFormVisible = false">确 定</el-button>
      </div>
    </el-dialog>
  </div>
</template>

<script>
import Sticky from "@/components/Sticky";
export default {
  components: { Sticky },
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
        type: "",
        budFore: false,
        explanation: "",
        description: "",
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
          // uom: "box",
          qty: 23,
          curreny: "CNY",
          price: 100,
          subTotal: 200
          // reqDelivery: "2020-7-7",
          // accounting: "",
          // comments: ""
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
      formLabelWidth: "258px"
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
    submitRequest() {
      this.$router.push("/request/list");
    }
  }
};
</script>

<style lang="scss" scoped>
.app-container {
  .el-form-item {
    margin-bottom: 10px;
  }
  .el-row {
    margin-bottom: 10px;
    &:last-child {
      margin-bottom: 0;
    }
  }
  /deep/ .el-collapse-item__content {
    padding-bottom: 0;
  }
  .header {
    padding: 0 15px;
    height: 50px;
    line-height: 50px;
    width: 100%;
    background-color: #219ef6;
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: -webkit-sticky;
    position: sticky;
    top: 20px;
  }
}
</style>