<template>

<div class="all-container">

<div class="all-container-padding bg" >

<el-tabs v-model="activeName" @tab-click="handleClick">

<el-tab-pane label="基本信息" name="first">

<el-form :model="userlist" :rules="rules" ref="EditorUserForms">

<el-form-item label="用户名" prop="username" :label-width="formLabelWidth">

<el-col :span="8"> <el-input v-model="userlist.username" disabled ></el-input></el-col>

</el-form-item>

<el-form-item label="电话" prop="phone" :label-width="formLabelWidth">

<el-col :span="8"> <el-input v-model="userlist.phone" placeholder="请输入电话"></el-input></el-col>

</el-form-item>

<el-form-item label="用户角色" prop="role_name" :label-width="formLabelWidth">

<el-col :span="8">

<el-input v-model="userlist.full_name" disabled ></el-input>

</el-col>

</el-form-item>

</el-form>

<div class="grid-content bg-purple">

<el-button type="primary" @click="EditorUserClick('userlist')" >保存</el-button>

</div>

</el-tab-pane>


<el-form :model="ruleForm" :rules="rules" ref="ruleFormRef">
               <el-form-item label="原密码" prop="pass" :label-width="formLabelWidth">
                     <el-col :span="8">   
                        <el-input v-model="ruleForm.pass" placeholder="请输入原密码" type="password"></el-input>
                    </el-col>
               </el-form-item>
               <el-form-item label="新密码" prop="newpass" :label-width="formLabelWidth">
                  <el-col :span="8">
                    <el-input v-model="ruleForm.newpass" placeholder="请输入新密码" id="newkey" type="password"></el-input>
                  </el-col>
               </el-form-item>
               <el-form-item label="重复新密码" prop="checknewpass" :label-width="formLabelWidth">
                  <el-col :span="8">   
              <el-input v-model="ruleForm.checknewpass" placeholder="请再次输入新密码" id='newkey1' type="password"></el-input>
                  </el-col>
                </el-form-item>
                </el-form>
                <div class="grid-content bg-purple">
                <el-button type="primary"  @click="submitForm('ruleFormRef')">保存</el-button>
                </div>
          <!-- </el-tab-pane> -->

</el-tabs>

</div>

</div>

</template>
<script>
export default {
                data() {
            var validatePass2 = (rule, value, callback) => {
           if (value === "") {
            callback(new Error("请再次输入密码"));
          } else if (value !== this.ruleForm.newpass) {
           callback(new Error("两次输入密码不一致!"));
            } else {
            callback();
          }
        };
           return {
               rules:{
             pass: [ { required: true, message: "请输入密码" } ],
            newpass: [ { required: true, message: "请输入新密码" } ],
            checknewpass: [ { required: true, validator: validatePass2, trigger: "blur" } ]
}
}
                }
}
</script>