<template>
  <div>
    <a-table
            rowKey="pid"
            :columns="ColumnsData"
            :pagination="false"
            :data-source="dataList"
            :scroll="{ x: 0, y: 390  }"
    >
    <span slot="status" slot-scope="elapsedCpuTime, record">
      <span style="padding: 4px;background: gold;color: #fff;">{{ elapsedCpuTime }} </span>
    </span>
    <span slot="status" slot-scope="status,record">

        <span v-if="status == progressStatus.INITREADY">
         未到达
        </span>
    </span>
<!--  <span slot="action" slot-scope="text, record">-->
<!--    <a-button type="primary" @click="showModal(record)">-->
<!--      I/O-->
<!--    </a-button>-->
<!--    <a-button type="danger" @click="pending(record)">-->
<!--      挂起-->
<!--    </a-button>-->
<!--    </span>-->
    </a-table>

  </div>
</template>
<script>
  import Policy from "../../model/Policy";

  let  currStatus = '';
import columns from "@/model/Column"
import { mapGetters, mapActions,mapMutations } from 'vuex';
import progressStatus from "@/mixin/progressStatus"
export default {
  name: "initList",
  mixins:[progressStatus],
  data() {
    return {
      Policy
    };
  },
  methods:{
  },
  computed:{
    ColumnsData(){
      if(this.getSchedulingPolicy === Policy.HRRF ) {
        return columns;
      } else {
        return columns.filter((item, index)=> {
          return item.dataIndex !== 'hrrf' && item.dataIndex !== 'ioTime'
        })
      }
    },
    ...mapGetters({
        dataList: 'initQueue'
    })
  }
};
</script>
