<template>
  <el-tabs v-model="activeName" @tab-click="handleClick">
    <el-tab-pane label="CPU百分比" name="CPUUtilization"><DataView/></el-tab-pane>
    <el-tab-pane label="专有网络公网流出带宽" name="VPC_PublicIP_InternetOutRate"><DataView/></el-tab-pane>
    <el-tab-pane label="专有网络公网流出带宽使用率" name="VPC_PublicIP_InternetOutRate_Percent"><DataView/></el-tab-pane>
  </el-tabs>
</template>
<script>
  import DataView from './DataTable.vue'
  import { mapState, mapMutations } from 'vuex'
  
  export default {
    data() {
      return {
        activeName: this.$store.state.metric
      }
    },
    methods: {
      ...mapMutations([
        'setMetric'
      ]),
      handleClick(tab, event) {
        this.setMetric(this.activeName)
      }
    },
    components: {
      DataView
    }
  };
</script>