<template>
  <div>
    <h1>{{ title }}</h1>
    <el-dialog title="Information" :visible.sync="dialogVisible" width="30%">
      <p>First Name: {{ codeContact.firstname }}</p>
      <p>Last Name: {{ codeContact.lastname }}</p>
      <p>Email: {{ codeContact.email }}</p>
      <p>Subject Title: {{ codeContact.subject }}</p>
      <p>Claim Request: {{ codeContact.desc }}</p>
      <p>Agreement: {{ codeContact.type ? "true" : "false" }}</p>
    </el-dialog>
    <el-form
      v-show="!dialogVisible"
      :model="codeContact"
      :rules="rules"
      ref="codeContact"
      label-width="120px"
      class="demo-codeContact"
    >
      <el-form-item label="First Name" prop="firstname">
        <el-input v-model="codeContact.firstname"></el-input>
      </el-form-item>
      <el-form-item label="Last Name" prop="lastname">
        <el-input v-model="codeContact.lastname"></el-input>
      </el-form-item>
      <el-form-item label="Email" prop="email">
        <el-input v-model="codeContact.email"></el-input>
      </el-form-item>
      <el-form-item label="Subject Title" prop="subject">
        <el-input v-model="codeContact.subject"></el-input>
      </el-form-item>
      <el-form-item label="Claim Request" prop="claim">
        <el-input type="textarea" v-model="codeContact.desc"></el-input>
      </el-form-item>
      <el-form-item label="Agreement" prop="type">
        <el-checkbox-group v-model="codeContact.type">
          <el-checkbox label="Please agree to the terms"></el-checkbox>
        </el-checkbox-group>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="submitForm('codeContact')"
          >Submit</el-button
        >
        <el-button @click="resetForm('codeContact')">Reset</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "Online Claim Request Form",
      dialogVisible: false,
      animal: "cat",
      codeContact: {
        firstname: "",
        lastname: "",
        email: "",
        subject: "",
        type: [],
        desc: ""
      },
      rules: {
        firstname: [
          {
            required: true,
            message: "Please input first name",
            trigger: "blur"
          }
        ],
        lastname: [
          {
            required: true,
            message: "Please input last name",
            trigger: "blur"
          }
        ],
        email: [
          {
            required: true,
            message: "Please input email",
            trigger: "blur"
          }
        ],
        subject: [
          {
            required: true
          },
          {
            required: true,
            max: 30,
            message: "Cannot be more than 30 words",
            trigger: "blur"
          }
        ],
        claim: [
          {
            required: false
          }
        ],
        type: [
          {
            type: "array",
            required: true,
            message: "Please agree to the terms",
            trigger: "blur"
          }
        ],
        desc: [
          {
            required: true,
            trigger: "blur"
          }
        ]
      }
    };
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate(valid => {
        if (valid) {
          this.dialogVisible = true;
        } else {
          this.dialogVisible = false;
          console.log("error submit!!");
          return false;
        }
      });
    },
    resetForm(formName) {
      this.$refs[formName].resetFields();
    }
  }
};
</script>
