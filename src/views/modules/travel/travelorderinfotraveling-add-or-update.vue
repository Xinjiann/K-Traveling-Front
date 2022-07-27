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
    <el-form-item label="" prop="orderPhonePrefix">
      <el-input v-model="dataForm.orderPhonePrefix" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="orderPhone">
      <el-input v-model="dataForm.orderPhone" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="orderWechat">
      <el-input v-model="dataForm.orderWechat" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="orderEmail">
      <el-input v-model="dataForm.orderEmail" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="startPlace">
      <el-input v-model="dataForm.startPlace" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="startPostcode">
      <el-input v-model="dataForm.startPostcode" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="startTime">
      <el-input v-model="dataForm.startTime" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="targetPlace">
      <el-input v-model="dataForm.targetPlace" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="targetPostcode">
      <el-input v-model="dataForm.targetPostcode" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="travelTime">
      <el-input v-model="dataForm.travelTime" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="budget">
      <el-input v-model="dataForm.budget" placeholder=""></el-input>
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
          orderPhonePrefix: '',
          orderPhone: '',
          orderWechat: '',
          orderEmail: '',
          startPlace: '',
          startPostcode: '',
          startTime: '',
          targetPlace: '',
          targetPostcode: '',
          travelTime: '',
          budget: '',
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
          orderPhonePrefix: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          orderPhone: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          orderWechat: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          orderEmail: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          startPlace: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          startPostcode: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          startTime: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          targetPlace: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          targetPostcode: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          travelTime: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          budget: [
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
              url: this.$http.adornUrlService(`/ktravel/travelorderinfotraveling/info/${this.dataForm.orderId}`),
              method: 'get',
              params: this.$http.adornParams()
            }).then(({data}) => {
              if (data && data.code === 0) {
                this.dataForm.id = data.travelOrderInfoTraveling.id
                this.dataForm.userWxOpenid = data.travelOrderInfoTraveling.userWxOpenid
                this.dataForm.orderTime = data.travelOrderInfoTraveling.orderTime
                this.dataForm.orderPhonePrefix = data.travelOrderInfoTraveling.orderPhonePrefix
                this.dataForm.orderPhone = data.travelOrderInfoTraveling.orderPhone
                this.dataForm.orderWechat = data.travelOrderInfoTraveling.orderWechat
                this.dataForm.orderEmail = data.travelOrderInfoTraveling.orderEmail
                this.dataForm.startPlace = data.travelOrderInfoTraveling.startPlace
                this.dataForm.startPostcode = data.travelOrderInfoTraveling.startPostcode
                this.dataForm.startTime = data.travelOrderInfoTraveling.startTime
                this.dataForm.targetPlace = data.travelOrderInfoTraveling.targetPlace
                this.dataForm.targetPostcode = data.travelOrderInfoTraveling.targetPostcode
                this.dataForm.travelTime = data.travelOrderInfoTraveling.travelTime
                this.dataForm.budget = data.travelOrderInfoTraveling.budget
                this.dataForm.adultNumber = data.travelOrderInfoTraveling.adultNumber
                this.dataForm.childNumber = data.travelOrderInfoTraveling.childNumber
                this.dataForm.trunkNumber = data.travelOrderInfoTraveling.trunkNumber
                this.dataForm.customerName = data.travelOrderInfoTraveling.customerName
                this.dataForm.customerPhoneNum = data.travelOrderInfoTraveling.customerPhoneNum
                this.dataForm.customerWechat = data.travelOrderInfoTraveling.customerWechat
                this.dataForm.customerTrunkNum = data.travelOrderInfoTraveling.customerTrunkNum
                this.dataForm.backupName = data.travelOrderInfoTraveling.backupName
                this.dataForm.backupPhoneNum = data.travelOrderInfoTraveling.backupPhoneNum
                this.dataForm.isAdditionalService = data.travelOrderInfoTraveling.isAdditionalService
                this.dataForm.orderAmount = data.travelOrderInfoTraveling.orderAmount
                this.dataForm.orderStatus = data.travelOrderInfoTraveling.orderStatus
                this.dataForm.field1 = data.travelOrderInfoTraveling.field1
                this.dataForm.field2 = data.travelOrderInfoTraveling.field2
                this.dataForm.field3 = data.travelOrderInfoTraveling.field3
                this.dataForm.field4 = data.travelOrderInfoTraveling.field4
                this.dataForm.field5 = data.travelOrderInfoTraveling.field5
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
              url: this.$http.adornUrlService(`/ktravel/travelorderinfotraveling/${!this.dataForm.orderId ? 'save' : 'update'}`),
              method: 'post',
              data: this.$http.adornData({
                'id': this.dataForm.id,
                'userWxOpenid': this.dataForm.userWxOpenid,
                'orderId': this.dataForm.orderId || undefined,
                'orderTime': this.dataForm.orderTime,
                'orderPhonePrefix': this.dataForm.orderPhonePrefix,
                'orderPhone': this.dataForm.orderPhone,
                'orderWechat': this.dataForm.orderWechat,
                'orderEmail': this.dataForm.orderEmail,
                'startPlace': this.dataForm.startPlace,
                'startPostcode': this.dataForm.startPostcode,
                'startTime': this.dataForm.startTime,
                'targetPlace': this.dataForm.targetPlace,
                'targetPostcode': this.dataForm.targetPostcode,
                'travelTime': this.dataForm.travelTime,
                'budget': this.dataForm.budget,
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
