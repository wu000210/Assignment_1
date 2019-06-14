<template>

<div>
   <h1>Claim Request Form</h1>
  <el-dialog
  title="list"
  :visible.sync="dialogVisible"
  width="30%"
  >
  <p> First Name: {{ ruleForm.FirstName }}</p>
  <p> Last Name: {{ ruleForm.LastName }}</p>
  <p> Email: {{ ruleForm.Email }}</p>
  <p> SubjectTitle: {{ ruleForm.SubjectTitle }}</p>
  <p> agreement: {{ ruleForm.agreement ? "true" : "false" }}</p>
 
</el-dialog>
  
  <el-form
     v-show="!dialogVisible"
     :model="ruleForm" :rules="rules" ref="ruleForm" label-width="120px" class="demo-ruleForm">
  <el-form-item label="First name" prop="FirstName">
    <el-input v-model="ruleForm.FirstName"></el-input>
  </el-form-item>

  <el-form-item label="Last name" prop="LastName">
    <el-input v-model="ruleForm.LastName"></el-input>
  </el-form-item>

  <el-form-item label="Email" prop="Email">
    <el-input v-model="ruleForm.Email"></el-input>
  </el-form-item>

  <el-form-item label="Subject Title" prop="SubjectTitle">
    <el-input v-model="ruleForm.SubjectTitle"></el-input>
  </el-form-item>

  <el-form-item label="Claim form" prop="desc">
    <el-input type="textarea" v-model="ruleForm.desc"></el-input>
  </el-form-item>

  <el-form-item label="" prop="agreement">
   <el-checkbox v-model="ruleForm.agreement">Agreement</el-checkbox>
  </el-form-item>

  <el-form-item>
    <el-button type="primary" @click="submitForm('ruleForm')">Submit</el-button>
    <el-button @click="resetForm('ruleForm')">Reset</el-button>
  </el-form-item>
</el-form>
</div>
</template>

<script>
  export default {
    data() {
      return {
        dialogVisible: false,
        ruleForm: {
          FirstName: '',
          LastName: '',
          Email: '',
          SubjectTitle: '',
          agreement: [],
          desc: ''
        },
        rules: {
          FirstName: [
            { required: true, message: 'Please input first name', trigger: 'blur' },
          ],
          LastName: [
            { required: true, message: 'Please input last name', trigger: 'blur' },
          ],
           Email: [
            { required: true, message: 'Please input Email', trigger: 'blur' },
          ],
          SubjectTitle: [
            { required: true, message: 'Please input Subject Title', trigger: 'blur' },
            { min: 1, max: 30, message: 'Length should be 1 to 30', trigger: 'blur' }
          ],
          agreement: [
            { required: true, message: 'Please check the box to agree the term', trigger: 'blur' }
          ],
          desc: [
            { required: true, message: 'Please input claim form', trigger: 'blur' }
          ]
        },
      };
    },
    methods: {
      submitForm(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
           this.dialogVisible = true;
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      },
      resetForm(formName) {
        this.$refs[formName].resetFields();
      }
    }
  }
</script>
