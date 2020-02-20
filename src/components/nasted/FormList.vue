<template>
  <div>
    <el-form :model="form" ref="dynamicValidateForm" size="small">
      <el-form-item label="username" prop="username" :rules="[{required: true, message: 'Please input username'}]">
        <el-input v-model="form.username"></el-input>
      </el-form-item>
      <el-form-item label="password" prop="password" :rules="[{required: true, message: 'Please input username'}]">
        <el-input type="password" v-model="form.password"></el-input>
      </el-form-item>
      <el-form-item label="address" prop="address.name" :rules="[{required: true, message: 'Please input username'}]">
        <el-input v-model="form.address.name"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button @click="addItems">Add</el-button>
      </el-form-item>
      <el-form-item label="tag" 
        v-for="(item,index) in form.tags" :prop="'tags.'+index+'.tag'" 
        :key="index" 
        :rules="{required: true, message: 'Please input username'}">
        <el-input v-model="item.tag"></el-input>
        <el-button @click="delItem(index)">delete</el-button>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="submit">Submit</el-button>
        <el-button @click="reset">Reset</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>
<script>
export default {
  name:"FormList",
  data() {
    return {
      form:{
        username:null,
        password:null,
        address:{
          name:""
        },
        tags:[{
          name:null
        }]
      }
    }
  },
  methods:{
    submit() {
      this.$refs.dynamicValidateForm.validate((valid)=>{
        console.log(valid)
      })
    },
    addItems() {
      this.form.tags.push({
        tag:''
      })
    },
    delItem(val) {
      this.form.tags.splice(val,1)
    },
    reset() {
      this.$refs.dynamicValidateForm.resetFields()
    }
  }
}
</script>