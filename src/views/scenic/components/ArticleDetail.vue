<template>
  <div>
    <el-form
      ref="ruleForm"
      :model="ruleForm"
      :rules="rules"
      label-width="100px"
      class="demo-ruleForm"
      :label-position="right"
    >
      <el-form-item label="景点名称" prop="name" required>
        <el-col :span="11">
          <el-input v-model="ruleForm.name" />
        </el-col>
      </el-form-item>

      <el-form-item label="景点经度" required>
        <el-col :span="11">
          <el-form-item prop="longitude">
            <el-input v-model="longitude" placeholder="请输入内容" />
          </el-form-item>
        </el-col>
      </el-form-item>
      <el-form-item label="景点纬度" required>
        <el-col :span="11">
          <el-form-item prop="latitude">
            <el-input v-model="latitude" placeholder="请输入内容" />
          </el-form-item>
        </el-col>
      </el-form-item>
      <el-form-item label="景点标签" prop="type">
        <el-checkbox-group v-model="ruleForm.type" max="1">
          <el-checkbox label="风景名胜" name="type" />
          <el-checkbox label="休闲娱乐" name="type" />
          <el-checkbox label="人文历史" name="type" />
        </el-checkbox-group>
      </el-form-item>

      <el-form-item label="详细内容" prop="desc">
        <el-col :span="11">
          <el-input v-model="ruleForm.desc" type="textarea" autosize />
        </el-col>
      </el-form-item>
      <el-form-item>
        <el-upload
          class="upload-demo"
          action="https://jsonplaceholder.typicode.com/posts/"
          :on-preview="handlePreview"
          :on-remove="handleRemove"
          :file-list="fileList"
          list-type="picture"
        >
          <el-button size="small" type="primary">点击上传</el-button>
          <div slot="tip" class="el-upload__tip">只能上传jpg/png文件，且不超过500kb</div>
        </el-upload>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="submitForm('ruleForm')">立即创建</el-button>
        <el-button @click="resetForm('ruleForm')">重置</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>
<script>
export default {
  data() {
    return {
      ruleForm: {
        name: '',
        region: '',
        longitude: '',
        latitude: '',
        delivery: false,
        type: [],
        resource: '',
        desc: '',
        fileList: [
          {
            name: 'food.jpeg',
            url:
              'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'
          },
          {
            name: 'food2.jpeg',
            url:
              'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'
          }
        ]
      },
      rules: {
        name: [
          { required: true, message: '请输入活动名称', trigger: 'blur' },
          { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
        ],
        region: [
          { required: true, message: '请选择活动区域', trigger: 'change' }
        ],
        date1: [
          {
            type: 'date',
            required: true,
            message: '请选择日期',
            trigger: 'change'
          }
        ],
        date2: [
          {
            type: 'date',
            required: true,
            message: '请选择时间',
            trigger: 'change'
          }
        ],
        type: [
          {
            type: 'array',
            required: true,
            message: '请至少选择一个活动性质',
            trigger: 'change'
          }
        ],
        resource: [
          { required: true, message: '请选择活动资源', trigger: 'change' }
        ],
        desc: [{ required: true, message: '请填写活动形式', trigger: 'blur' }]
      }
    }
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate(valid => {
        if (valid) {
          alert('submit!')
        } else {
          console.log('error submit!!')
          return false
        }
      })
    },
    resetForm(formName) {
      this.$refs[formName].resetFields()
    },
    handleRemove(file, fileList) {
      console.log(file, fileList)
    },
    handlePreview(file) {
      console.log(file)
    }
  }
}
</script>

<style scoped>
.demo-ruleForm {
  margin-top: 80px;
  margin-left: 400px;
}
.upload-demo {
  width: 40%;
}
</style>

