<template>
  <el-dialog
    :title="!dataForm.id ? '新增' : '修改'"
    :close-on-click-modal="false"
    :visible.sync="visible">
    <el-form :model="dataForm" :rules="dataRule" ref="dataForm" @keyup.enter.native="dataFormSubmit()" label-width="80px">
    <el-form-item label="" prop="driverName">
      <el-input v-model="dataForm.driverName" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="driverLanguage">
      <el-input v-model="dataForm.driverLanguage" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="driverPhone">
      <el-input v-model="dataForm.driverPhone" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="driverEmail">
      <el-input v-model="dataForm.driverEmail" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="driverType">
      <el-input v-model="dataForm.driverType" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="driverCountry">
      <el-input v-model="dataForm.driverCountry" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="driverPhoto">
      <el-input v-model="dataForm.driverPhoto" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="driverStar">
      <el-input v-model="dataForm.driverStar" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="driverVideo">
      <el-input v-model="dataForm.driverVideo" placeholder=""></el-input>
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
          id: 0,
          driverName: '',
          driverLanguage: '',
          driverPhone: '',
          driverEmail: '',
          driverType: '',
          driverCountry: '',
          driverPhoto: '',
          driverStar: '',
          driverVideo: '',
          field1: '',
          field2: '',
          field3: '',
          field4: '',
          field5: ''
        },
        dataRule: {
          driverName: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          driverLanguage: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          driverPhone: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          driverEmail: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          driverType: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          driverCountry: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          driverPhoto: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          driverStar: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          driverVideo: [
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
        this.dataForm.id = id || 0
        this.visible = true
        this.$nextTick(() => {
          this.$refs['dataForm'].resetFields()
          if (this.dataForm.id) {
            this.$http({
              url: this.$http.adornUrlService(`/ktravel/traveldriverinfo/info/${this.dataForm.id}`),
              method: 'get',
              params: this.$http.adornParams()
            }).then(({data}) => {
              if (data && data.code === 0) {
                this.dataForm.driverName = data.travelDriverInfo.driverName
                this.dataForm.driverLanguage = data.travelDriverInfo.driverLanguage
                this.dataForm.driverPhone = data.travelDriverInfo.driverPhone
                this.dataForm.driverEmail = data.travelDriverInfo.driverEmail
                this.dataForm.driverType = data.travelDriverInfo.driverType
                this.dataForm.driverCountry = data.travelDriverInfo.driverCountry
                this.dataForm.driverPhoto = data.travelDriverInfo.driverPhoto
                this.dataForm.driverStar = data.travelDriverInfo.driverStar
                this.dataForm.driverVideo = data.travelDriverInfo.driverVideo
                this.dataForm.field1 = data.travelDriverInfo.field1
                this.dataForm.field2 = data.travelDriverInfo.field2
                this.dataForm.field3 = data.travelDriverInfo.field3
                this.dataForm.field4 = data.travelDriverInfo.field4
                this.dataForm.field5 = data.travelDriverInfo.field5
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
              url: this.$http.adornUrlService(`/ktravel/traveldriverinfo/${!this.dataForm.id ? 'save' : 'update'}`),
              method: 'post',
              data: this.$http.adornData({
                'id': this.dataForm.id || undefined,
                'driverName': this.dataForm.driverName,
                'driverLanguage': this.dataForm.driverLanguage,
                'driverPhone': this.dataForm.driverPhone,
                'driverEmail': this.dataForm.driverEmail,
                'driverType': this.dataForm.driverType,
                'driverCountry': this.dataForm.driverCountry,
                'driverPhoto': this.dataForm.driverPhoto,
                'driverStar': this.dataForm.driverStar,
                'driverVideo': this.dataForm.driverVideo,
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
