<template>
  <div class="app-container">
    <el-row :gutter="10">
      <el-col :span="12">
        <div>
          <el-card>
            <div style="display:flex;justify-content:space-around;">
              <router-link to="/request/new">
                <div class="box">
                  <img src="@/assets/home/new-pr.png" alt />
                  <span>New Request</span>
                  <span></span>
                </div>
              </router-link>
              <router-link to="/request/list">
              <div class="box">
                <img src="@/assets/home/request-list.png" alt />
                <span>Request List</span>
                <span></span>
              </div>
              </router-link>
              <router-link to="/request/list_approval">
              <div class="box">
                <img src="@/assets/home/approval-list.png" alt />
                <span>Approval List</span>
                <span></span>
              </div>
              </router-link>
              <router-link to="/request/list_approved">
              <div class="box">
                <img src="@/assets/home/approved-list.png" alt />
                <span>Approved List</span>
                <span></span>
              </div>
              </router-link>
            </div>
          </el-card>
        </div>
      </el-col>
      <el-col :span="12">
        <el-card>
          <el-calendar v-model="value"></el-calendar>
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>
<script>
export default {
  name:"Dashboard",
  data() {
    return { value: new Date() };
  }
};
</script>
<style lang="scss" scoped>
.box {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-around;
  width: 150px;
  height: 150px;
  margin: 0;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.12);
  img {
    width: 48px;
    height: 48px;
  }
}
</style>