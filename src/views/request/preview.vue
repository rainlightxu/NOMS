<template>
  <div class="app-container">
    <div class="header">
      <el-page-header @back="goBack">
        <template slot="content">
          <span>Purchase Request: [ Preview - PR000000343261, Processing ]</span>
        </template>
      </el-page-header>
      <div>
        <el-button v-loading="loading" style="margin-left: 10px;" type="success">Print</el-button>
        <el-button v-loading="loading" type="warning">Export</el-button>
      </div>
    </div>
    <reqForm></reqForm>
  </div>
</template>

<script>
import ReqForm from "./components/reqForm";
export default {
  components: { ReqForm },
  data() {
    return {
      loading: false
    };
  },
  methods: {
    handleChange(val) {
      console.log(val);
    },
    onSubmit() {
      console.log("submit!");
    },
    submitRequest() {
      this.$router.push("/request/list");
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