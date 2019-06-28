<template>
  <div class="app-container">
    
    <div class="table-container">
      <div class="table-top-bar clearfix">
        <div class="fl">
            <el-tooltip class="item" effect="dark" content="编辑" placement="top" >
              <i class="el-icon-pencil" @click="open">
              </i>
            </el-tooltip>
            <el-tooltip class="item" effect="dark" content="删除" placement="top">
              <i class="el-icon-bin">
              </i>
            </el-tooltip>
            <el-tooltip class="item" effect="dark" content="批准" placement="top">
              <i class="el-icon-check_circle">
              </i>
            </el-tooltip>
            <el-tooltip class="item" effect="dark" content="拒绝" placement="top">
              <i class="el-icon-blocked">
              </i>
            </el-tooltip>
        </div>
      </div>
      <el-table
    :data="tableData"
    show-header
                stripe
                border
                fit
    style="width: 100%">
    <el-table-column type="expand">
      <template slot-scope="props">
        <div style="font-size:18px;color:#333;padding-bottom:20px;">销售人员/CG拜访记录对比（上月及本月）</div> 
        <el-form label-position="left"  class="demo-table-expand">
          <el-form-item label="销售人员拜访记录：" style="font-size:16px;color:#666"></el-form-item>
          <el-form-item label="签到时间">
            <span>{{ props.row.shop }}</span>
          </el-form-item>
          <el-form-item label="签退时间">
            <span>{{ props.row.id }}</span>
          </el-form-item>
          <el-form-item label="滞留时间">
            <span>{{ props.row.shopId }}</span>
          </el-form-item>
          <el-form-item label="有效拜访次数">
            <span>{{ props.row.category }}</span>
          </el-form-item>
          <el-form-item label="签到照片">
            <el-popover trigger="click" placement="top" class="avatar" >
                <img height="500" src="../../assets/images/carabao-logo-big.png" alt="图片">
                <div slot="reference" class="name-wrapper">
                  <img  src="../../assets/images/carabao-logo-big.png" alt="图片" class="avatar">
                </div>
              </el-popover>
          </el-form-item>
          <el-form-item label="签退照片">
            <el-popover trigger="click" placement="top" class="avatar" >
                <img height="500" src="../../assets/images/carabao-logo-big.png" alt="图片">
                <div slot="reference" class="name-wrapper">
                  <img  src="../../assets/images/carabao-logo-big.png" alt="图片" class="avatar">
                </div>
              </el-popover>
          </el-form-item>
        </el-form>
        <el-form label-position="left"  class="demo-table-expand">
          <el-form-item label="CG拜访记录：" style="font-size:16px;color:#666"></el-form-item>
          <el-form-item label="签到时间">
            <span>{{ props.row.shop }}</span>
          </el-form-item>
          <el-form-item label="签退时间">
            <span>{{ props.row.id }}</span>
          </el-form-item>
          <el-form-item label="滞留时间">
            <span>{{ props.row.shopId }}</span>
          </el-form-item>
          <el-form-item label="有效拜访次数">
            <span>{{ props.row.category }}</span>
          </el-form-item>
          <el-form-item label="签到照片">
            <el-popover trigger="click" placement="top" class="avatar" >
                <img height="500" src="../../assets/images/carabao-logo-big.png" alt="图片">
                <div slot="reference" class="name-wrapper">
                  <img  src="../../assets/images/carabao-logo-big.png" alt="图片" class="avatar">
                </div>
              </el-popover>
          </el-form-item>
          <el-form-item label="签退照片">
            <el-popover trigger="click" placement="top" class="avatar" >
                <img height="500" src="../../assets/images/carabao-logo-big.png" alt="图片">
                <div slot="reference" class="name-wrapper">
                  <img  src="../../assets/images/carabao-logo-big.png" alt="图片" class="avatar">
                </div>
              </el-popover>
          </el-form-item>
        </el-form>
      </template>
    </el-table-column>
    <el-table-column
      label="终端编号"
      prop="id">
    </el-table-column>
    <el-table-column
      label="终端名称"
      prop="name">
    </el-table-column>
    <el-table-column
      label="终端类型"
      prop="name33">
    </el-table-column>
    <el-table-column
      label="大区"
      prop="name">
    </el-table-column>
    <el-table-column
      label="分公司"
      prop="name">
    </el-table-column>
    <el-table-column
      label="办事处"
      prop="name">
    </el-table-column>
    <el-table-column
      label="拜访员工工号"
      prop="desc">
    </el-table-column>
    <el-table-column
      label="拜访员工"
      prop="desc">
    </el-table-column>
    <el-table-column
      label="员工类型"
      prop="desc22">
    </el-table-column>
    <el-table-column
      label="拜访时间"
      prop="desc">
    </el-table-column>
    <el-table-column
      label="创建时间"
      prop="desc">
    </el-table-column>
    <el-table-column
      label="状态"
      prop="desc">
    </el-table-column>
  </el-table>

    </div>

    <div class="pagination-wrapper">
      <el-pagination
                     :current-page="1"
                     :page-sizes="[100, 200, 300, 400]"
                     :page-size="100"
                     layout="total, sizes, prev, pager, next, jumper"
                     :total="400">
      </el-pagination>
    </div>

    <el-dialog title="门店信息" :visible.sync="dialogVisible" width="1200px">
        <el-form :model="formData"  ref="shopForm" label-width="100px" inline class="demo-ruleForm">
          <el-form-item label="门店编号" prop="name">
            <el-input v-model="formData.code" disabled></el-input>
          </el-form-item>
          <el-form-item label="门店名称" prop="name">
            <el-input v-model="formData.name" disabled></el-input>
          </el-form-item>
          <el-form-item label="门店展示" prop="shopUrlList">
              <el-popover trigger="click" placement="top" class="avatar" >
                <img height="500" src="../../assets/images/carabao-logo-big.png" alt="图片">
                <div slot="reference" class="name-wrapper">
                  <img  src="../../assets/images/carabao-logo-big.png" alt="图片" class="avatar">
                </div>
              </el-popover>
              <el-popover trigger="click" placement="top" class="avatar" >
                <img height="500" src="../../assets/images/carabao-logo-big.png" alt="图片">
                <div slot="reference" class="name-wrapper">
                  <img  src="../../assets/images/carabao-logo-big.png" alt="图片" class="avatar">
                </div>
              </el-popover>
              <el-popover trigger="click" placement="top" class="avatar" >
                <img height="500" src="../../assets/images/carabao-logo-big.png" alt="图片">
                <div slot="reference" class="name-wrapper">
                  <img  src="../../assets/images/carabao-logo-big.png" alt="图片" class="avatar">
                </div>
              </el-popover>  
              <!-- <img v-if="formData.shopPhotos" :src="formData.shopPhotos" class="avatar">    
              <img v-if="formData.shopkeeperPhotos" :src="formData.shopkeeperPhotos" class="avatar">     -->
          </el-form-item>
          <el-form-item label="店主姓名">
            <el-input v-model="formData.shopkeeper" disabled></el-input>
          </el-form-item>
          <el-form-item label="联系电话" prop="contactNumber">
            <el-input v-model="formData.contactNumber" disabled></el-input>
          </el-form-item>
          <el-form-item label="微信号" prop="contactNumber">
            <el-input v-model="formData.wechatNumber" disabled></el-input>
          </el-form-item>
          <el-form-item label="电子邮件" prop="email">
            <el-input v-model="formData.email" disabled></el-input>
          </el-form-item>
          <el-form-item label="渠道类型" prop="name">
            <el-input v-model="formData.channelName" disabled></el-input>
          </el-form-item>
          <el-form-item label="终端类型" prop="name">
            <el-input v-model="formData.shopTypeName" disabled></el-input>
          </el-form-item>
          <el-form-item label="大区" prop="name">
              <el-input v-model="formData.regionName" disabled></el-input>
          </el-form-item>
          <el-form-item label="组织机构">
            <el-input v-model="formData.orgName" disabled></el-input>
          </el-form-item>
          <el-form-item label="省" >
            <el-input v-model="formData.province" disabled></el-input>
          </el-form-item>
          <el-form-item label="市" >
            <el-input v-model="formData.city" disabled></el-input>
          </el-form-item>
          <el-form-item label="区" prop="name" >
            <el-input v-model="formData.districtName" disabled></el-input>
          </el-form-item>
          <el-form-item label="地址" prop="name" >
            <el-input v-model="formData.address" style="width:200px" disabled>
              <template slot="append"><i class="el-icon-location" ></i></template>
            </el-input>
          </el-form-item>
          <el-form-item label="经纬度" >
            <el-input v-model="formData.latlng" disabled></el-input>
          </el-form-item>
          <el-form-item label="油站编码" >
            <el-input v-model="formData.postcode" disabled></el-input>
          </el-form-item>
          <el-form-item label="经销商" >
            <el-input v-model="formData.dealerName" disabled></el-input>
          </el-form-item>
          <el-form-item label="备注" prop="name" >
            <el-input
              type="textarea"
              :autosize = "{minRows: 6, maxRows: 8}"
              maxlength="100"
              style="width:200px;"
              v-model="formData.remark" disabled></el-input>
          </el-form-item>
        </el-form>
    </el-dialog>

    <success-confirm ref="successConfirm" @confirm="successConfirm"></success-confirm>
    <failed-confirm ref="failedConfirm" @confirm="failedConfirm"></failed-confirm>
    <warning-confirm ref="warningConfirm" @confirm="warningConfirm"></warning-confirm>
  </div>
</template>

<script>
  export default {
    name: 'demo',
    data() {
      return {
        successVisible: true,
        failedVisible:true,
        dialogVisible: false,
        tableKey: 0,
        orderCount: null,
        listLoading: false,
        tableData: [{
          name: '',
          category: '',
          name33:'门店/经销商',
          desc: '',
          address: '',
          shop: '',
          shopId2: '',
          shopId3: '',
          shopId4: '',
          desc22:'销售人员/CG'
        },{
          name: '',
          category: '',
          desc: '',
          address: '',
          shop: '',
          shopId2: '',
          shopId3: '',
          shopId4: '',
          desc22:'销售人员/CG'
        },{
          name: '',
          category: '',
          desc: '',
          address: '',
          shop: '',
          shopId2: '',
          shopId3: '',
          shopId4: '',
          desc22:'销售人员/CG'
        }],
        list: [
          {
            date: '2016-05-03',
            name: '王小虎',
            province: '上海',
            city: '普陀区',
            address: '上海市普陀区金沙江路 1518 弄',
            zip: 200333
          }, {
            date: '2016-05-02',
            name: '王小虎',
            province: '上海',
            city: '普陀区',
            address: '上海市普陀区金沙江路 1518 弄',
            zip: 200333
          }, {
            date: '2016-05-04',
            name: '王小虎',
            province: '上海',
            city: '普陀区',
            address: '上海市普陀区金沙江路 1518 弄',
            zip: 200333
          }, {
            date: '2016-05-01',
            name: '王小虎',
            province: '上海',
            city: '普陀区',
            address: '上海市普陀区金沙江路 1518 弄',
            zip: 200333
          }, {
            date: '2016-05-03',
            name: '王小虎',
            province: '上海',
            city: '普陀区',
            address: '上海市普陀区金沙江路 1518 弄',
            zip: 200333
          }, {
            date: '2016-05-02',
            name: '王小虎',
            province: '上海',
            city: '普陀区',
            address: '上海市普陀区金沙江路 1518 弄',
            zip: 200333
          }, {
            date: '2016-05-04',
            name: '王小虎',
            province: '上海',
            city: '普陀区',
            address: '上海市普陀区金沙江路 1518 弄',
            zip: 200333
          }, {
            date: '2016-05-01',
            name: '王小虎',
            province: '上海',
            city: '普陀区',
            address: '上海市普陀区金沙江路 1518 弄',
            zip: 200333
          }
        ],
        countQuery: {},
        listQuery: {},
        searchQuery: {},
        source: [
          {name: '全部', value: 0},
          {name: '小程序', value: 1},
          {name: '微信', value: 2}
        ],
        orderCount: {
          all: 300,
          close: 20,
          paying: 20,
          paid: 20,
          delivery: 20,
          over: 20,
          refund: 20,
        },
        orderType: [
          {name: '全部', value: 0},
          {name: '团购', value: 1},
          {name: '秒杀', value: 2}
        ],
        pickerOptions1: {
          disabledDate(time) {
            return time.getTime() > Date.now();
          },
          shortcuts: [{
            text: '今天',
            onClick(picker) {
              picker.$emit('pick', new Date());
            }
          }, {
            text: '昨天',
            onClick(picker) {
              const date = new Date();
              date.setTime(date.getTime() - 3600 * 1000 * 24);
              picker.$emit('pick', date);
            }
          }, {
            text: '一周前',
            onClick(picker) {
              const date = new Date();
              date.setTime(date.getTime() - 3600 * 1000 * 24 * 7);
              picker.$emit('pick', date);
            }
          }]
        },
        downloadLoading: false,
        temp: {
          id: undefined,
          importance: 1,
          remark: '',
          timestamp: new Date(),
          title: '',
          type: '',
          status: 'published'
        },
        formData:{},
        ruleForm: {
          name: '1213',
          region: '',
          date1: '',
          date2: '',
          delivery: false,
          type: [],
          resource: '',
          desc: ''
        },
        rules: {
          name: [
            {required: true, message: '请输入活动名称', trigger: 'blur'},
            {min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur'}
          ],
          region: [
            {required: true, message: '请选择活动区域', trigger: 'change'}
          ],
          date1: [
            {type: 'date', required: true, message: '请选择日期', trigger: 'change'}
          ],
          date2: [
            {type: 'date', required: true, message: '请选择时间', trigger: 'change'}
          ],
          type: [
            {type: 'array', required: true, message: '请至少选择一个活动性质', trigger: 'change'}
          ],
          resource: [
            {required: true, message: '请选择活动资源', trigger: 'change'}
          ],
          desc: [
            {required: true, message: '请填写活动形式', trigger: 'blur'}
          ]
        }
      }
    },
    created() {
      this.getData()
    },
    methods: {
      getData() {
        // this.listLoading = true
        // fetchOrderCount(this.countQuery).then(res => {
        //   // console.log(res)
        //   this.orderCount = res.data
        // })
      },
      open(){
        this.dialogVisible = true;
        console.log(1);
      },
      handleDownload() {
        this.downloadLoading = true
        import('@/vendor/Export2Excel').then(excel => {
          const tHeader = ['timestamp', 'title', 'type', 'importance', 'status']
          const filterVal = ['timestamp', 'title', 'type', 'importance', 'status']
          const data = this.formatJson(filterVal, this.list)
          excel.export_json_to_excel({
            header: tHeader,
            data,
            filename: 'table-list'
          })
          this.downloadLoading = false
        })
      },
      handleRowClick(row, event, column) {
        this.dialogVisible = true
      },
      showSuccess() {
        this.$refs.successConfirm.show()
      },
      showfailed(){
        this.$refs.failedConfirm.show()
      },
      showWarning(){
        this.$refs.warningConfirm.show()
      },
      successConfirm(){
        // alert('成功确认')
      },
      failedConfirm(){
        // alert('失败确认')
      },
      warningConfirm(){
        // alert('警告确认')
      }
    },
    components: {
    }
  }
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
  .aa {
    padding: 0 5px;
    color: #dcdfe6;
  }
  .demo-table-expand{
    float: left;
    width: 50%;
  }
  .el-form--inline .el-form-item{
    width: 46%;
  }
  .avatar {
    width: 78px;
    height: 78px;
    display: inline-block;
    margin-right: 30px;
  }
</style>
