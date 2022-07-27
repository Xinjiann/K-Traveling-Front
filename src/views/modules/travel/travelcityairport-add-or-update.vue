<template>
  <el-dialog
    :title="!dataForm.id ? '新增' : '修改'"
    :close-on-click-modal="false"
    :visible.sync="visible">
    <el-form :model="dataForm" :rules="dataRule" ref="dataForm" @keyup.enter.native="dataFormSubmit()" label-width="80px">
    <el-form-item label="" prop="cityName">
      <el-input v-model="dataForm.cityName" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="cityPostcode">
      <el-input v-model="dataForm.cityPostcode" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="cityAirport">
      <el-input v-model="dataForm.cityAirport" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="isTerminal">
      <el-input v-model="dataForm.isTerminal" placeholder=""></el-input>
    </el-form-item>
    <el-form-item label="" prop="terminalNo">
      <el-input v-model="dataForm.terminalNo" placeholder=""></el-input>
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
          cityName: '',
          cityPostcode: '',
          cityAirport: '',
          isTerminal: '',
          terminalNo: '',
          field1: '',
          field2: '',
          field3: '',
          field4: '',
          field5: ''
        },
        dataRule: {
          cityName: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          cityPostcode: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          cityAirport: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          isTerminal: [
            { required: true, message: '不能为空', trigger: 'blur' }
          ],
          terminalNo: [
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
              url: this.$http.adornUrlService(`/ktravel/travelcityairport/info/${this.dataForm.id}`),
              method: 'get',
              params: this.$http.adornParams()
            }).then(({data}) => {
              if (data && data.code === 0) {
                this.dataForm.cityName = data.travelCityAirport.cityName
                this.dataForm.cityPostcode = data.travelCityAirport.cityPostcode
                this.dataForm.cityAirport = data.travelCityAirport.cityAirport
                this.dataForm.isTerminal = data.travelCityAirport.isTerminal
                this.dataForm.terminalNo = data.travelCityAirport.terminalNo
                this.dataForm.field1 = data.travelCityAirport.field1
                this.dataForm.field2 = data.travelCityAirport.field2
                this.dataForm.field3 = data.travelCityAirport.field3
                this.dataForm.field4 = data.travelCityAirport.field4
                this.dataForm.field5 = data.travelCityAirport.field5
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
              url: this.$http.adornUrlService(`/ktravel/travelcityairport/${!this.dataForm.id ? 'save' : 'update'}`),
              method: 'post',
              data: this.$http.adornData({
                'id': this.dataForm.id || undefined,
                'cityName': this.dataForm.cityName,
                'cityPostcode': this.dataForm.cityPostcode,
                'cityAirport': this.dataForm.cityAirport,
                'isTerminal': this.dataForm.isTerminal,
                'terminalNo': this.dataForm.terminalNo,
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
