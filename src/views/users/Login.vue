<template>
  <div class="login">
    <el-form
      :model="ruleForm"
      status-icon
      :rules="rules"
      ref="ruleForm"
      label-width="0px"
      class="demo-ruleForm"
    >
      <el-form-item>
        <h1>B2C电商管理系统</h1>
      </el-form-item>
      <el-form-item prop="question">
        <el-select v-model="ruleForm.question" placeholder="请选择密保问题">
          <el-option
            v-for="item in answer"
            :key="item.value"
            :label="item.label"
            :value="item.value"
          >
          </el-option>
        </el-select>
      </el-form-item>
      <el-form-item label="" prop="answer">
        <el-input
          type="text"
          placeholder="请输入密保答案"
          prefix-icon="el-icon-key"
          clearable
          v-model="ruleForm.answer"
          autocomplete="off"
        ></el-input>
      </el-form-item>
      <el-form-item label="" prop="uname">
        <el-input
          type="text"
          placeholder="请输入密保用户名"
          prefix-icon="el-icon-user"
          clearable
          v-model="ruleForm.uname"
          autocomplete="off"
        ></el-input>
      </el-form-item>
      <el-form-item label="" prop="pwd">
        <el-input
          type="password"
          placeholder="请输入密码"
          prefix-icon="el-icon-lock"
          show-password
          clearable
          v-model="ruleForm.pwd"
        ></el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="submitForm('ruleForm')"
          >提交</el-button
        >
      </el-form-item>
    </el-form>
  </div>
</template>
<script>
export default {
  data() {
    return {
      //密保问题
      answer: [
        { value: "你奶奶的名字叫什么", label: "你奶奶的名字叫什么" },
        { value: "你爸爸的名字叫什么", label: "你爸爸的名字叫什么" },
        { value: "你其中一位老师的名字", label: "你其中一位老师的名字" },
      ],
      //表单数据
      ruleForm: {
        qusetion: "",
        answer: "",
        uname: "",
        pwd: "",
      },
      rules: {
        //键：表单数据的键
        //值-数组 里面是一个个对象 对应一个个验证规则
        question: [
          { required: true, message: "请选择密保问题", trigger: "blur" },
        ],
        answer: [
          { required: true, message: "请输入密保答案", trigger: "blur" },
          { min: 2, max: 8, message: "长度在 2 到 8 个字符", trigger: "blur" },
        ],
        uname: [
          { required: true, message: "请输入用户名", trigger: "blur" },
          { min: 2, max: 8, message: "长度在 2 到 8 个字符", trigger: "blur" },
        ],
        pwd: [
          { required: true, message: "请输入密码", trigger: "blur" },
          { min: 2, max: 8, message: "长度在 2 到 8 个字符", trigger: "blur" },
        ],
      },
    };
  },
  methods: {
    //提交验证
    submitForm(formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          alert("submit!");
        } else {
          console.log("error submit!!");
          return false;
        }
      });
    },
  },
};
</script>
<style lang="scss" scoped>
.login {
  width: 100%;
  height: 100%;
  background: brown;
  display: flex;
  justify-content: center;
  align-items: center;
}
.el-form {
  width: 300px;
  height: 372px;
  //   background: white;
  .el-select {
    width: 100%;
  }
  h1 {
    text-align: center;
    color: white;
  }
  .el-button {
    width: 100%;
  }
}
</style>