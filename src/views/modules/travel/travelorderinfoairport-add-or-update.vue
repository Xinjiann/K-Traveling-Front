<template>
  <el-dialog
    :title="!dataForm.orderId ? '新增' : '修改'"
    :close-on-click-modal="false"
    :visible.sync="visible">
    <el-form :model="dataForm" :rules="dataRule" ref="dataForm" @keyup.enter.native="dataFormSubmit()" label-width="80px">
    <el-form-item label="" prop="id">
      <el-input v-model="dataForm.id" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="userWxOpenid">
      <el-input v-model="dataForm.userWxOpenid" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="orderTime">
      <el-input v-model="dataForm.orderTime" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="orderType">
      <el-input v-model="dataForm.orderType" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="orderCity">
      <el-input v-model="dataForm.orderCity" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="flightNumber">
      <el-input v-model="dataForm.flightNumber" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="pickupTime">
      <el-input v-model="dataForm.pickupTime" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="targetPlace">
      <el-input v-model="dataForm.targetPlace" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="targetPostcode">
      <el-input v-model="dataForm.targetPostcode" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="adultNumber">
      <el-input v-model="dataForm.adultNumber" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="childNumber">
      <el-input v-model="dataForm.childNumber" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="trunkNumber">
      <el-input v-model="dataForm.trunkNumber" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="customerName">
      <el-input v-model="dataForm.customerName" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="customerPhoneNum">
      <el-input v-model="dataForm.customerPhoneNum" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="customerWechat">
      <el-input v-model="dataForm.customerWechat" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="customerTrunkNum">
      <el-input v-model="dataForm.customerTrunkNum" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="backupName">
      <el-input v-model="dataForm.backupName" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="backupPhoneNum">
      <el-input v-model="dataForm.backupPhoneNum" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="isAdditionalService">
      <el-input v-model="dataForm.isAdditionalService" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="orderAmount">
      <el-input v-model="dataForm.orderAmount" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="orderStatus">
      <el-input v-model="dataForm.orderStatus" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="field1">
      <el-input v-model="dataForm.field1" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="field2">
      <el-input v-model="dataForm.field2" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="field3">
      <el-input v-model="dataForm.field3" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="field4">
      <el-input v-model="dataForm.field4" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="field5">
      <el-input v-model="dataForm.field5" placeholder=""></el-input>
    </el-form-item>
    </el-form>
    <span slot="footer" class="dialog-footer">
      <el-button @click="visible = false">取消</el-button>
      <el-button type="primary" @click="dataFormSubmit()">确定</el-button>
    </span>
  </el-dialog>
</template>

<script>
  export default {
    data () {
      return {
        visible: false,
        dataForm: {
          id: '',
          userWxOpenid: '',
          orderId: 0,
          orderTime: '',
          orderType: '',
          orderCity: '',
          flightNumber: '',
          pickupTime: '',
          targetPlace: '',
          targetPostcode: '',
          adultNumber: '',
          childNumber: '',
          trunkNumber: '',
          customerName: '',
          customerPhoneNum: '',
          customerWechat: '',
          customerTrunkNum: '',
          backupName: '',
          backupPhoneNum: '',
          isAdditionalService: '',
          orderAmount: '',
          orderStatus: '',
          field1: '',
          field2: '',
          field3: '',
          field4: '',
          field5: ''
        },
        dataRule: {
          id: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          userWxOpenid: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          orderTime: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          orderType: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          orderCity: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          flightNumber: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          pickupTime: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          targetPlace: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          targetPostcode: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          adultNumber: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          childNumber: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          trunkNumber: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          customerName: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          customerPhoneNum: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          customerWechat: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          customerTrunkNum: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          backupName: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          backupPhoneNum: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          isAdditionalService: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          orderAmount: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          orderStatus: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          field1: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          field2: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          field3: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          field4: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          field5: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ]
        }
      }
    },
    methods: {
      init (id) {
        this.dataForm.orderId = id || 0
        this.visible = true
        this.$nextTick(() => {
          this.$refs['dataForm'].resetFields()
          if (this.dataForm.orderId) {
            this.$http({
              url: this.$http.adornUrlService(`/ktravel/travelorderinfoairport/info/${this.dataForm.orderId}`),
              method: 'get',
              params: this.$http.adornParams()
            }).then(({data}) => {
              if (data && data.code === 0) {
                this.dataForm.id = data.travelOrderInfoAirport.id
                this.dataForm.userWxOpenid = data.travelOrderInfoAirport.userWxOpenid
                this.dataForm.orderTime = data.travelOrderInfoAirport.orderTime
                this.dataForm.orderType = data.travelOrderInfoAirport.orderType
                this.dataForm.orderCity = data.travelOrderInfoAirport.orderCity
                this.dataForm.flightNumber = data.travelOrderInfoAirport.flightNumber
                this.dataForm.pickupTime = data.travelOrderInfoAirport.pickupTime
                this.dataForm.targetPlace = data.travelOrderInfoAirport.targetPlace
                this.dataForm.targetPostcode = data.travelOrderInfoAirport.targetPostcode
                this.dataForm.adultNumber = data.travelOrderInfoAirport.adultNumber
                this.dataForm.childNumber = data.travelOrderInfoAirport.childNumber
                this.dataForm.trunkNumber = data.travelOrderInfoAirport.trunkNumber
                this.dataForm.customerName = data.travelOrderInfoAirport.customerName
                this.dataForm.customerPhoneNum = data.travelOrderInfoAirport.customerPhoneNum
                this.dataForm.customerWechat = data.travelOrderInfoAirport.customerWechat
                this.dataForm.customerTrunkNum = data.travelOrderInfoAirport.customerTrunkNum
                this.dataForm.backupName = data.travelOrderInfoAirport.backupName
                this.dataForm.backupPhoneNum = data.travelOrderInfoAirport.backupPhoneNum
                this.dataForm.isAdditionalService = data.travelOrderInfoAirport.isAdditionalService
                this.dataForm.orderAmount = data.travelOrderInfoAirport.orderAmount
                this.dataForm.orderStatus = data.travelOrderInfoAirport.orderStatus
                this.dataForm.field1 = data.travelOrderInfoAirport.field1
                this.dataForm.field2 = data.travelOrderInfoAirport.field2
                this.dataForm.field3 = data.travelOrderInfoAirport.field3
                this.dataForm.field4 = data.travelOrderInfoAirport.field4
                this.dataForm.field5 = data.travelOrderInfoAirport.field5
              }
            })
          }
        })
      },
      // 表单提交
      dataFormSubmit () {
        this.$refs['dataForm'].validate((valid) => {
          if (valid) {
            this.$http({
              url: this.$http.adornUrlService(`/ktravel/travelorderinfoairport/${!this.dataForm.orderId ? 'save' : 'update'}`),
              method: 'post',
              data: this.$http.adornData({
                'id': this.dataForm.id,
                'userWxOpenid': this.dataForm.userWxOpenid,
                'orderId': this.dataForm.orderId || undefined,
                'orderTime': this.dataForm.orderTime,
                'orderType': this.dataForm.orderType,
                'orderCity': this.dataForm.orderCity,
                'flightNumber': this.dataForm.flightNumber,
                'pickupTime': this.dataForm.pickupTime,
                'targetPlace': this.dataForm.targetPlace,
                'targetPostcode': this.dataForm.targetPostcode,
                'adultNumber': this.dataForm.adultNumber,
                'childNumber': this.dataForm.childNumber,
                'trunkNumber': this.dataForm.trunkNumber,
                'customerName': this.dataForm.customerName,
                'customerPhoneNum': this.dataForm.customerPhoneNum,
                'customerWechat': this.dataForm.customerWechat,
                'customerTrunkNum': this.dataForm.customerTrunkNum,
                'backupName': this.dataForm.backupName,
                'backupPhoneNum': this.dataForm.backupPhoneNum,
                'isAdditionalService': this.dataForm.isAdditionalService,
                'orderAmount': this.dataForm.orderAmount,
                'orderStatus': this.dataForm.orderStatus,
                'field1': this.dataForm.field1,
                'field2': this.dataForm.field2,
                'field3': this.dataForm.field3,
                'field4': this.dataForm.field4,
                'field5': this.dataForm.field5
              })
            }).then(({data}) => {
              if (data && data.code === 0) {
                this.$message({
                  message: '操作成功',
                  type: 'success',
                  duration: 1500,
                  onClose: () => {
                    this.visible = false
                    this.$emit('refreshDataList')
                  }
                })
              } else {
                this.$message.error(data.msg)
              }
            })
          }
        })
      }
    }
  }
</script>
