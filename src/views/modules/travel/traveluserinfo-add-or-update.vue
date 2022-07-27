<template>
  <el-dialog
    :title="!dataForm.userWxOpenid ? '新增' : '修改'"
    :close-on-click-modal="false"
    :visible.sync="visible">
    <el-form :model="dataForm" :rules="dataRule" ref="dataForm" @keyup.enter.native="dataFormSubmit()" label-width="80px">
    <el-form-item label="" prop="userName">
      <el-input v-model="dataForm.userName" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="userFirstName">
      <el-input v-model="dataForm.userFirstName" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="userLastName">
      <el-input v-model="dataForm.userLastName" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="userWxNumber">
      <el-input v-model="dataForm.userWxNumber" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="userStatus">
      <el-input v-model="dataForm.userStatus" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="userPastOrder">
      <el-input v-model="dataForm.userPastOrder" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="userPhoneNumber">
      <el-input v-model="dataForm.userPhoneNumber" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="userPhonePrefix">
      <el-input v-model="dataForm.userPhonePrefix" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="userPassword">
      <el-input v-model="dataForm.userPassword" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="userEmail">
      <el-input v-model="dataForm.userEmail" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="registrationDate">
      <el-input v-model="dataForm.registrationDate" placeholder=""></el-input>
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
          userWxOpenid: 0,
          userName: '',
          userFirstName: '',
          userLastName: '',
          userWxNumber: '',
          userStatus: '',
          userPastOrder: '',
          userPhoneNumber: '',
          userPhonePrefix: '',
          userPassword: '',
          userEmail: '',
          registrationDate: '',
          field1: '',
          field2: '',
          field3: '',
          field4: '',
          field5: ''
        },
        dataRule: {
          userName: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          userFirstName: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          userLastName: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          userWxNumber: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          userStatus: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          userPastOrder: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          userPhoneNumber: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          userPhonePrefix: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          userPassword: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          userEmail: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          registrationDate: [
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
        this.dataForm.userWxOpenid = id || 0
        this.visible = true
        this.$nextTick(() => {
          this.$refs['dataForm'].resetFields()
          if (this.dataForm.userWxOpenid) {
            this.$http({
              url: this.$http.adornUrlService(`/ktravel/traveluserinfo/info/${this.dataForm.userWxOpenid}`),
              method: 'get',
              params: this.$http.adornParams()
            }).then(({data}) => {
              if (data && data.code === 0) {
                this.dataForm.userName = data.travelUserInfo.userName
                this.dataForm.userFirstName = data.travelUserInfo.userFirstName
                this.dataForm.userLastName = data.travelUserInfo.userLastName
                this.dataForm.userWxNumber = data.travelUserInfo.userWxNumber
                this.dataForm.userStatus = data.travelUserInfo.userStatus
                this.dataForm.userPastOrder = data.travelUserInfo.userPastOrder
                this.dataForm.userPhoneNumber = data.travelUserInfo.userPhoneNumber
                this.dataForm.userPhonePrefix = data.travelUserInfo.userPhonePrefix
                this.dataForm.userPassword = data.travelUserInfo.userPassword
                this.dataForm.userEmail = data.travelUserInfo.userEmail
                this.dataForm.registrationDate = data.travelUserInfo.registrationDate
                this.dataForm.field1 = data.travelUserInfo.field1
                this.dataForm.field2 = data.travelUserInfo.field2
                this.dataForm.field3 = data.travelUserInfo.field3
                this.dataForm.field4 = data.travelUserInfo.field4
                this.dataForm.field5 = data.travelUserInfo.field5
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
              url: this.$http.adornUrlService(`/ktravel/traveluserinfo/${!this.dataForm.userWxOpenid ? 'save' : 'update'}`),
              method: 'post',
              data: this.$http.adornData({
                'userWxOpenid': this.dataForm.userWxOpenid || undefined,
                'userName': this.dataForm.userName,
                'userFirstName': this.dataForm.userFirstName,
                'userLastName': this.dataForm.userLastName,
                'userWxNumber': this.dataForm.userWxNumber,
                'userStatus': this.dataForm.userStatus,
                'userPastOrder': this.dataForm.userPastOrder,
                'userPhoneNumber': this.dataForm.userPhoneNumber,
                'userPhonePrefix': this.dataForm.userPhonePrefix,
                'userPassword': this.dataForm.userPassword,
                'userEmail': this.dataForm.userEmail,
                'registrationDate': this.dataForm.registrationDate,
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
