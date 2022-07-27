<template>
  <el-dialog
    :title="!dataForm.id ? '新增' : '修改'"
    :close-on-click-modal="false"
    :visible.sync="visible">
    <el-form :model="dataForm" :rules="dataRule" ref="dataForm" @keyup.enter.native="dataFormSubmit()" label-width="80px">
    <el-form-item label="" prop="carName">
      <el-input v-model="dataForm.carName" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="carMake">
      <el-input v-model="dataForm.carMake" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="carModel">
      <el-input v-model="dataForm.carModel" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="carColor">
      <el-input v-model="dataForm.carColor" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="carRegistration">
      <el-input v-model="dataForm.carRegistration" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="carPassengers">
      <el-input v-model="dataForm.carPassengers" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="carType">
      <el-input v-model="dataForm.carType" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="carPhoto">
      <el-input v-model="dataForm.carPhoto" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="carVideo">
      <el-input v-model="dataForm.carVideo" placeholder=""></el-input>
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
          carName: '',
          carMake: '',
          carModel: '',
          carColor: '',
          carRegistration: '',
          carPassengers: '',
          carType: '',
          carPhoto: '',
          carVideo: '',
          field1: '',
          field2: '',
          field3: '',
          field4: '',
          field5: ''
        },
        dataRule: {
          carName: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          carMake: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          carModel: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          carColor: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          carRegistration: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          carPassengers: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          carType: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          carPhoto: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          carVideo: [
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
              url: this.$http.adornUrlService(`/ktravel/travelvehicleinfo/info/${this.dataForm.id}`),
              method: 'get',
              params: this.$http.adornParams()
            }).then(({data}) => {
              if (data && data.code === 0) {
                this.dataForm.carName = data.travelVehicleInfo.carName
                this.dataForm.carMake = data.travelVehicleInfo.carMake
                this.dataForm.carModel = data.travelVehicleInfo.carModel
                this.dataForm.carColor = data.travelVehicleInfo.carColor
                this.dataForm.carRegistration = data.travelVehicleInfo.carRegistration
                this.dataForm.carPassengers = data.travelVehicleInfo.carPassengers
                this.dataForm.carType = data.travelVehicleInfo.carType
                this.dataForm.carPhoto = data.travelVehicleInfo.carPhoto
                this.dataForm.carVideo = data.travelVehicleInfo.carVideo
                this.dataForm.field1 = data.travelVehicleInfo.field1
                this.dataForm.field2 = data.travelVehicleInfo.field2
                this.dataForm.field3 = data.travelVehicleInfo.field3
                this.dataForm.field4 = data.travelVehicleInfo.field4
                this.dataForm.field5 = data.travelVehicleInfo.field5
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
              url: this.$http.adornUrlService(`/ktravel/travelvehicleinfo/${!this.dataForm.id ? 'save' : 'update'}`),
              method: 'post',
              data: this.$http.adornData({
                'id': this.dataForm.id || undefined,
                'carName': this.dataForm.carName,
                'carMake': this.dataForm.carMake,
                'carModel': this.dataForm.carModel,
                'carColor': this.dataForm.carColor,
                'carRegistration': this.dataForm.carRegistration,
                'carPassengers': this.dataForm.carPassengers,
                'carType': this.dataForm.carType,
                'carPhoto': this.dataForm.carPhoto,
                'carVideo': this.dataForm.carVideo,
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
