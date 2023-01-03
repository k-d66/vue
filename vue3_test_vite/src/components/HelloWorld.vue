<!--
<template>
  <h1>{{ msg }}</h1>
  <button @click="count++">count is: {{ count }}</button>
  <p>Edit <code>components/HelloWorld.vue</code> to test hot module replacement.</p>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      count: 0
    }
  }
}
</script>
-->


<!--<template>
  <div style="height: 100%;background: #FFFFFF;overflow-y: hidden">
    <TitleBar title="经营信息"></TitleBar>
    <div class="info_bar">
      <div style="padding-left: 20px">
        <span style="">
          <van-icon name="user-circle-o" size="32" color="#1798F0"/>
          <span style="color: #808080;font-size: 20px;padding-left: 10px">{{cifName}}</span>
        </span>
        <span style="padding-left: 50px">
          <span style="color: #808080;font-size: 20px;">证件号：{{idNo}}</span>
        </span>
      </div>
      <div style="color: rgba(153, 153, 153, 0.996078431372549);padding-right: 20px">

      </div>
    </div>
    <div style="padding: 0px 20px;">
      <div class="answer_bar">
        <div style="font-size: 18px;color: #333333;">经营信息共<span style="color: #f59a23;font-size: 23px">{{data.length}}</span>项调查内容</div>
      </div>
      &lt;!&ndash;家庭成员展示页面&ndash;&gt;
      <div v-for="(item,index) in data" :key="index">
        <div style="display: flex;justify-content: space-between">
          <div style="font-size: 22px;color: #333333;font-weight: 500">
            {{index +1 }}、{{item.qus_desc}}
          </div>
          <div style="padding-right: 20px" @click="add">
            <van-icon name="add-o" color="#f59a23" size="25px"/><span style="padding-left: 8px">新增</span>
          </div>
        </div>
        <div class="card_area">
          <div style="border: 1px solid #DDD;border-radius: 10px;margin-bottom: 20px;" v-for="(item1,index1) in manageInfo" :key="index1">
            <div class="card_title">
              <div style="display: flex;padding-left: 20px;align-items: center">
                <div style="height: 20px;width: 6px;background: #00a3ff;"></div>
                <span style="padding-left: 8px;font-weight: 700;font-size: 20px;">经营信息 - {{item1.license}}</span>
              </div>
              <div style="display: flex;padding-right: 20px">
                <div style="padding-right: 20px" @click="edit(item1)"><van-icon name="edit" color="#f59a23" size="25px"/><span>编辑</span></div>
                <div @click="del(item1)"><van-icon name="delete-o" color="#f59a23" size="25px"/><span>删除</span></div>
              </div>
            </div>
            <div style="display: flex;flex-direction: column;padding: 20px 30px;">
              <div style="display: flex;height: 60px;align-items: center">
                <div style="flex: 1;display: flex;align-items: center">
                  <div style="font-size: 19px;color: #000000;flex: 2;">{{ item.ids.license }}</div>
                  <div style="flex: 3;position: relative;">
                    <div class="input" >{{item1.license}}</div>
                  </div>
                </div>
                <div style="flex: 1;display: flex;align-items: center">
                  <div style="font-size: 19px;color: #000000;flex: 2;">{{ item.ids.principal }}</div>
                  <div style="flex: 3;">
                    <div class="input" >{{transCode(item1.principal,'regType')}}</div>
                  </div>
                </div>
              </div>
              <div style="display: flex;height: 60px;align-items: center">
                <div style="flex: 1;display: flex;align-items: center">
                  <div style="font-size: 19px;color: #000000;flex: 2;">{{ item.ids.if_smallcorp }}</div>
                  <div style="flex: 3;position: relative;">
                    <div class="input" >{{item1.if_smallcorp}}</div>
                  </div>
                </div>
                <div style="flex: 1;display: flex;align-items: center">
                  <div style="font-size: 19px;color: #000000;flex: 2;">{{ item.ids.reg_addr }}</div>
                  <div style="flex: 3;position: relative;">
                    <div class="input" >{{transCode(item1.reg_addr,'main_bus')}}</div>
                  </div>
                </div>
              </div>
              <div style="display: flex;height: 60px;align-items: center">
                <div style="flex: 1;display: flex;align-items: center">
                  <div style="font-size: 19px;color: #000000;flex: 2;">{{ item.ids.business_entity }}</div>
                  <div style="flex: 3;position: relative;">
                    <div class="input" >{{item1.business_entity}}</div>
                  </div>
                </div>
                <div style="flex: 1;display: flex;align-items: center">
                  <div style="font-size: 19px;color: #000000;flex: 2;">{{ item.ids.newagr }}</div>
                  <div style="flex: 3;position: relative;">
                    <div class="input" >{{transCode(item1.newagr,'agriType')}}</div>
                  </div>
                </div>
              </div>
              <div style="display: flex;height: 60px;align-items: center">
                <div style="flex: 1;display: flex;align-items: center">
                  <div style="font-size: 19px;color: #000000;flex: 2;">{{ item.ids.simu_bus }}</div>
                  <div style="flex: 3;position: relative;">
                    <div class="input" >{{transCode(item1.simu_bus,'agriBus')}}</div>
                  </div>
                </div>
                <div style="flex: 1;display: flex;align-items: center">
                  <div style="font-size: 19px;color: #000000;flex: 2;">{{ item.ids.main_bus }}</div>
                  <div style="flex: 3;position: relative;">
                    <div class="input" >{{item1.main_bus}}</div>
                  </div>
                </div>
              </div>
              <div style="display: flex;height: 60px;align-items: center">
                <div style="flex: 1;display: flex;align-items: center">
                  <div style="font-size: 19px;color: #000000;flex: 2;">{{ item.ids.prod_mang_id }}</div>
                  <div style="flex: 3;position: relative;">
                    <div class="input" >{{item1.prod_mang_id}}</div>
                  </div>
                </div>
                <div style="flex: 1;display: flex;align-items: center">
                  <div style="font-size: 19px;color: #000000;flex: 2;">{{ item.ids.reg_beg_date }}</div>
                  <div style="flex: 3;position: relative;">
                    <div class="input" >{{formatDate(item1.reg_beg_date)}}</div>
                  </div>
                </div>
              </div>
              <div style="display: flex;height: 60px;align-items: center">
                <div style="flex: 1;display: flex;align-items: center">
                  <div style="font-size: 19px;color: #000000;flex: 2;">{{ item.ids.begin_date }}</div>
                  <div style="flex: 3;position: relative;">
                    <div class="input" >{{formatDate(item1.begin_date)}}</div>
                  </div>
                </div>
                <div style="flex: 1;display: flex;"></div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import {getCifPersProdByPage,delCifPersProd} from "@/components/interFace/customerInterface/customerInterface";
  import {formatDate} from "@/public/js/date.util";
  export default {
    name: "manageInfoView",
    data () {
      return {
        customer: {},
        manageInfo: [],
        famType: [], //家族关系
        cifName:'',
        cifNo:'',
        idNo: '',
        data: [{
          qus_desc: '经营信息',
          type: 'list',
          ids: {
            // 2020.06.18修改 整理布局
            license: '营业执照号', //营业执照号
            principal: '营业执照性质', //营业执照性质
            if_smallcorp: '是否小微企业主', //是否小微企业主
            reg_addr: '经营场所', //经营场所
            business_entity:'经营主体名称',
            newagr: '新型农业主体类型', //新型农业主体类型
            simu_bus: '新型农业主体主营业务', //新型农业主体主营业务
            main_bus: '经营范围', //经营范围
            prod_mang_id: '经营id', //经营id
            reg_beg_date: '营业执照注册时间', //营业执照注册时间
            begin_date: '实际经营起始时间'  //实际经营起始时间
          }
        }]
      }
    },
    mounted() {
      console.log(this.$store.getters["customerManager/getParams"]);
      this.famType = this.dataDics.getOptions('fam_type');
      this.customer = this.$store.getters["customerManager/getParams"];
      this.cifName = this.customer.cif_name;
      this.cifNo = this.customer.cif_no;
      this.idNo = this.customer.id_no;
      console.log(this.customer);
      this.selectList()
    },
    methods: {
      selectList() {
        // 查询基本信息
        getCifPersProdByPage({
          cif_no: this.cifNo,
          pageNo: 1,
          pageSize: 10
        },res => {
          console.log(res);
          this.manageInfo = res;
          this.manageInfo.forEach(item => {
            if (item.if_smallcorp == '0') {
              item.if_smallcorp = '否'
            }else if (item.if_smallcorp == '1') {
              item.if_smallcorp = '是'
            }
          })
        })
      },
      // 格式化日期
      formatDate(val) {
        console.log(val);
        if (val == '') return val
        let value = formatDate(val);
        return value
      },
      // 字典项转码
      transCode(val,s_field) {
        if (val == "") {
          return val
        }
        let value = this.dataDics.getText(val,s_field);
        return value
      },
      add () {
        console.log('add')
        this.$router.push({name: 'addManageInfoView'})
      },
      edit (item) {
        console.log(item);
        this.$store.commit('customerManager/setManageInfo',item);
        this.$router.push({name: 'editManageInfoView'})
        console.log('add')
      },
      del (item) {
        this.NativeUI.confirm({message: '您确认删除该记录吗？'}).then(() => {
          console.log('delete')
          delCifPersProd({
            prod_mang_id: item.prod_mang_id
          },res => {
            console.log(res);
            this.selectList();
          })
        }).catch((err) => {
          console.log('cancel')
        })
      },
      look () {
        console.log('look');
        this.show = true
      },
      join(index) {
        console.log(index);
        this.page = index;
        this.show = false;
      }
    }
  };
</script>

<style scoped>
  .info_bar {
    background: #ffffff;
    height: 56px;
    line-height: 56px;
    border-bottom: 1px solid rgba(242, 242, 242, 1);
    display: flex;
    justify-content: space-between
  }
  .answer_bar {
    display: flex;
    justify-content: space-between;
    height: 64px;
    line-height: 64px
  }
  .card_area {
    padding: 20px;
    width: 100%;
    height: calc(100vh - 64px - 56px - 64px - 33px);
    overflow-y: scroll;
  }
  .card_title {
    display: flex;
    justify-content: space-between;
    border-bottom: 1px solid #DDD;
    height: 60px;
    align-items: center
  }
  .input {
    height: 50px;
    line-height: 50px;
    width: 90%;
    font-size: 19px;
    color: #000;
    border: 0.5px solid #DDD;
    padding-left: 8px;
  }
</style>-->

<template>
  <div style="height: 100%;background: #FFFFFF;overflow-y: hidden">
    <TitleBar title="经营信息"></TitleBar>
    <div class="info_bar">
      <div style="padding-left: 20px">
        <span style="">
          <van-icon name="user-circle-o" size="32" color="#1798F0"/>
          <span style="color: #808080;font-size: 20px;padding-left: 10px">{{cifName}}</span>
        </span>
        <span style="padding-left: 50px">
          <span style="color: #808080;font-size: 20px;">证件号：{{idNo}}</span>
        </span>
      </div>
      <div style="color: rgba(153, 153, 153, 0.996078431372549);padding-right: 20px">

      </div>
    </div>
    <!--    <div style="padding: 0px 20px;display:none">
          <div class="answer_bar">
            <div style="font-size: 18px;color: #333333;">经营信息共<span style="color: #f59a23;font-size: 23px">{{data.length}}</span>项调查内容</div>
          </div>
          &lt;!&ndash;家庭成员展示页面&ndash;&gt;
          <div v-for="(item,index) in data" :key="index" >
            <div style="display: flex;justify-content: space-between">
              <div style="font-size: 22px;color: #333333;font-weight: 500">
                {{index +1 }}、{{item.qus_desc}}
              </div>
              <div style="padding-right: 20px" @click="add">
                <van-icon name="add-o" color="#f59a23" size="25px"/><span style="padding-left: 8px">新增</span>
              </div>
            </div>
            <div class="card_area" style="display:none">
              <div style="border: 1px solid #DDD;border-radius: 10px;margin-bottom: 20px;" v-for="(item1,index1) in manageInfo" :key="index1">
                <div class="card_title">
                  <div style="display: flex;padding-left: 20px;align-items: center">
                    <div style="height: 20px;width: 6px;background: #00a3ff;"></div>
                    <span style="padding-left: 8px;font-weight: 700;font-size: 20px;">经营信息 - {{item1.license}}</span>
                  </div>
                  <div style="display: flex;padding-right: 20px">
                    <div style="padding-right: 20px" @click="edit(item1)"><van-icon name="edit" color="#f59a23" size="25px"/><span>编辑</span></div>
                    <div @click="del(item1)"><van-icon name="delete-o" color="#f59a23" size="25px"/><span>删除</span></div>
                  </div>
                </div>
                <div style="display: flex;flex-direction: column;padding: 20px 30px;">
                  <div style="display: flex;height: 60px;align-items: center">
                    <div style="flex: 1;display: flex;align-items: center">
                      <div style="font-size: 19px;color: #000000;flex: 2;">{{ item.ids.license }}</div>
                      <div style="flex: 3;position: relative;">
                        <div class="input" >{{item1.license}}</div>
                      </div>
                    </div>
                    <div style="flex: 1;display: flex;align-items: center">
                      <div style="font-size: 19px;color: #000000;flex: 2;">{{ item.ids.principal }}</div>
                      <div style="flex: 3;">
                        <div class="input" >{{transCode(item1.principal,'regType')}}</div>
                      </div>
                    </div>
                  </div>
                  <div style="display: flex;height: 60px;align-items: center">
                    <div style="flex: 1;display: flex;align-items: center">
                      <div style="font-size: 19px;color: #000000;flex: 2;">{{ item.ids.if_smallcorp }}</div>
                      <div style="flex: 3;position: relative;">
                        <div class="input" >{{item1.if_smallcorp}}</div>
                      </div>
                    </div>
                    <div style="flex: 1;display: flex;align-items: center">
                      <div style="font-size: 19px;color: #000000;flex: 2;">{{ item.ids.reg_addr }}</div>
                      <div style="flex: 3;position: relative;">
                        <div class="input" >{{transCode(item1.reg_addr,'main_bus')}}</div>
                      </div>
                    </div>
                  </div>
                  <div style="display: flex;height: 60px;align-items: center">
                    <div style="flex: 1;display: flex;align-items: center">
                      <div style="font-size: 19px;color: #000000;flex: 2;">{{ item.ids.business_entity }}</div>
                      <div style="flex: 3;position: relative;">
                        <div class="input" >{{item1.business_entity}}</div>
                      </div>
                    </div>
                    <div style="flex: 1;display: flex;align-items: center">
                      <div style="font-size: 19px;color: #000000;flex: 2;">{{ item.ids.newagr }}</div>
                      <div style="flex: 3;position: relative;">
                        <div class="input" >{{transCode(item1.newagr,'agriType')}}</div>
                      </div>
                    </div>
                  </div>
                  <div style="display: flex;height: 60px;align-items: center">
                    <div style="flex: 1;display: flex;align-items: center">
                      <div style="font-size: 19px;color: #000000;flex: 2;">{{ item.ids.simu_bus }}</div>
                      <div style="flex: 3;position: relative;">
                        <div class="input" >{{transCode(item1.simu_bus,'agriBus')}}</div>
                      </div>
                    </div>
                    <div style="flex: 1;display: flex;align-items: center">
                      <div style="font-size: 19px;color: #000000;flex: 2;">{{ item.ids.main_bus }}</div>
                      <div style="flex: 3;position: relative;">
                        <div class="input" >{{item1.main_bus}}</div>
                      </div>
                    </div>
                  </div>
                  <div style="display: flex;height: 60px;align-items: center">
                    <div style="flex: 1;display: flex;align-items: center">
                      <div style="font-size: 19px;color: #000000;flex: 2;">{{ item.ids.prod_mang_id }}</div>
                      <div style="flex: 3;position: relative;">
                        <div class="input" >{{item1.prod_mang_id}}</div>
                      </div>
                    </div>
                    <div style="flex: 1;display: flex;align-items: center">
                      <div style="font-size: 19px;color: #000000;flex: 2;">{{ item.ids.reg_beg_date }}</div>
                      <div style="flex: 3;position: relative;">
                        <div class="input" >{{formatDate(item1.reg_beg_date)}}</div>
                      </div>
                    </div>
                  </div>
                  <div style="display: flex;height: 60px;align-items: center">
                    <div style="flex: 1;display: flex;align-items: center">
                      <div style="font-size: 19px;color: #000000;flex: 2;">{{ item.ids.begin_date }}</div>
                      <div style="flex: 3;position: relative;">
                        <div class="input" >{{formatDate(item1.begin_date)}}</div>
                      </div>
                    </div>
                    <div style="flex: 1;display: flex;"></div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>-->
    <!-- table展示区 -->
    <div class="infoView">
      <div class="header-item">
        <div class="left-item">
          经营信息
        </div>
        <div class="right-item">
          <div  @click="add">
            <van-icon name="add-o" color="#f59a23" size="25px"/>新增
          </div>
        </div>
      </div>
      <div class="section-view">
        <!-- 后期v-for  外循环遍历经营信息1 2 3-->
        <div >
          <div class="card-title">
            <div class="title">经营信息</div>
            <div class="more-btn">
              <div style="padding-right: 20px" @click="edit(item1)"><van-icon name="edit" color="#f59a23" size="25px"/><span>编辑</span>
              </div>
              <div @click="del(item1)">
                <van-icon name="delete-o" color="#f59a23" size="25px"/><span>删除</span>
              </div>
              <div >
                <van-icon name="comment" /><span>详情</span>
              </div>
            </div>
          </div>
          <div class="card-contert">
            <!--内循环 遍历数据展示 -->
            <div class="row-item">
              <div class="left-item">经营者ID：</div>
              <div class="right-item">121321342143</div>
            </div>
            <div class="row-item">
              <div class="left-item">经营者ID：</div>
              <div class="right-item">121321342143</div>
            </div>
            <div class="row-item">
              <div class="left-item">经营者ID：</div>
              <div class="right-item">121321342143</div>
            </div>
            <div class="row-item">
              <div class="left-item">经营者ID：</div>
              <div class="right-item">121321342143</div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- 弹框表单 -->
    <van-popup v-model="showManager">
      <addManageInfoView></addManageInfoView>


    </van-popup>

  </div>
</template>

<script>
import {
  getCifPersProdByPage,
  delCifPersProd,
} from "@/components/interFace/customerInterface/customerInterface";
import { formatDate } from "@/public/js/date.util";
import addManageInfoView from './editManageInfoView.vue'
export default {
  name: "manageInfoView",
  components:{
    addManageInfoView
  },
  data () {
    return {
      customer: {},
      manageInfo: [],
      famType: [], //家族关系
      cifName:'',
      cifNo:'',
      idNo: '',
      data: [{
        qus_desc: '经营信息',
        type: 'list',
        ids: {
          // 2020.06.18修改 整理布局
          license: '营业执照号', //营业执照号
          principal: '营业执照性质', //营业执照性质
          if_smallcorp: '是否小微企业主', //是否小微企业主
          reg_addr: '经营场所', //经营场所
          business_entity:'经营主体名称',
          newagr: '新型农业主体类型', //新型农业主体类型
          simu_bus: '新型农业主体主营业务', //新型农业主体主营业务
          main_bus: '经营范围', //经营范围
          prod_mang_id: '经营id', //经营id
          reg_beg_date: '营业执照注册时间', //营业执照注册时间
          begin_date: '实际经营起始时间'  //实际经营起始时间
        }
      }],
      showManager:false // 弹出框
    }
  },
  mounted() {
    console.log(this.$store.getters["customerManager/getParams"]);
    this.famType = this.dataDics.getOptions('fam_type');
    this.customer = this.$store.getters["customerManager/getParams"];
    this.cifName = this.customer.cif_name;
    this.cifNo = this.customer.cif_no;
    this.idNo = this.customer.id_no;
    console.log(this.customer);
    this.selectList()
  },
  methods: {
    selectList() {
      // 查询基本信息
      getCifPersProdByPage({
        cif_no: this.cifNo,
        pageNo: 1,
        pageSize: 10
      },res => {
        console.log(res);
        this.manageInfo = res;
        this.manageInfo.forEach(item => {
          if (item.if_smallcorp == '0') {
            item.if_smallcorp = '否'
          }else if (item.if_smallcorp == '1') {
            item.if_smallcorp = '是'
          }
        })
      })
    },
    // 格式化日期
    formatDate(val) {
      console.log(val);
      if (val == '') return val
      let value = formatDate(val);
      return value
    },
    // 字典项转码
    transCode(val,s_field) {
      if (val == "") {
        return val
      }
      let value = this.dataDics.getText(val,s_field);
      return value
    },
    add () {
      console.log('add')
      // this.$router.push({name: 'addManageInfoView'})

      this.showManager=true
    },
    edit (item) {
      console.log(item);
      this.$store.commit('customerManager/setManageInfo',item);
      this.$router.push({name: 'editManageInfoView'})
      console.log('add')
    },
    del (item) {
      this.NativeUI.confirm({message: '您确认删除该记录吗？'}).then(() => {
        console.log('delete')
        delCifPersProd({
          prod_mang_id: item.prod_mang_id
        },res => {
          console.log(res);
          this.selectList();
        })
      }).catch((err) => {
        console.log('cancel')
      })
    },
    look () {
      console.log('look');
      this.show = true
    },
    join(index) {
      console.log(index);
      this.page = index;
      this.show = false;
    }
  }
};
</script>

<style scoped>
.info_bar {
  background: #ffffff;
  height: 56px;
  line-height: 56px;
  border-bottom: 1px solid rgba(242, 242, 242, 1);
  display: flex;
  justify-content: space-between
}
.answer_bar {
  display: flex;
  justify-content: space-between;
  height: 64px;
  line-height: 64px
}
.card_area {
  padding: 20px;
  width: 100%;
  height: calc(100vh - 64px - 56px - 64px - 33px);
  overflow-y: scroll;
}
.card_title {
  display: flex;
  justify-content: space-between;
  border-bottom: 1px solid #DDD;
  height: 60px;
  align-items: center
}
.input {
  height: 50px;
  line-height: 50px;
  width: 90%;
  font-size: 19px;
  color: #000;
  border: 0.5px solid #DDD;
  padding-left: 8px;
}

</style>
<style scoped lang='less'>
.infoView{
  padding: 20px 50px;
  .header-item{
    display: flex;
    justify-content: space-between;
    margin: 15px  0;
    .left-item{
      border-left: 7px solid #409eff;
      padding-left: 5px;
      font-weight: bold;
    }
  }
  .section-view{
    background: #fff;
    box-shadow: rgba(0, 0, 0, 0.1) 0px 10px 50px;
    padding: 20px;
    border-radius: 5px;
    .card-title{
      display: flex;
      justify-content: space-between;
      .title{
        font-size: 16px;
        font-weight: bold;
      }
      .more-btn{
        display: flex;
        :nth-child(2){
          margin: 0 5px;
        }
      }
    }
    .card-contert{
      display: grid;
      grid-template-columns: 22% 22% 22% 22% 20%;
      grid-column-gap: 20px;
      .row-item{
        display: flex;
        .left-item{
          font-size: 14px;
          color: #999;
        }
        .right-item{
          color: #333;
        }

      }
    }
  }
}
</style>
