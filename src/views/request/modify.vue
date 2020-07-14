<template>
  <div class="app-container">
    <div class="header">
      <h2>Purchase Request: [ Edit - PR000000343258 ]</h2>
      <div>
        <el-button
          v-loading="loading"
          style="margin-left: 10px;"
          type="success"
          @click="submitRequest"
        >Save</el-button>
        <el-button v-loading="loading" type="warning" @click="cancelSubmit">Cancel</el-button>
      </div>
    </div>
    <reqForm ref="reqRef"></reqForm>
  </div>
</template>

<script>
import ReqForm from "./components/reqForm";
export default {
  components: { ReqForm },
  data() {
    return {
      loading:false
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
      console.log(this.$refs.reqRef)
      this.$router.push("/request/list");
    },
    cancelSubmit() {
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