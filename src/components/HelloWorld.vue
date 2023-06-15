<template>
    <div class="login_div">
   <el-form :model="form" label-width="120px" style="text-align: center" class="el_login">
	<el-form-item label="用户名">
		<el-input v-model="user" placeholder="请输入用户名" style="width:140px"></el-input>
    </el-form-item>  
	<el-form-item label="密码">
		<el-input v-model="password" placeholder="请输入密码" style="width:140px"></el-input>
    </el-form-item>  
  </el-form>
  <button @click="getData()">获取api数据</button>
  <div>
    <ul>
      <li v-for="item in items" :key="item.id">{{ item.title }}</li>
    </ul>
  </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
        items: [],
    };
  },
  methods:{
   getData(){
      var api="http://117.50.177.215:10093/v1/api/albums";
      //2.使用axios 进行get请求
      this.axios.get(api, {
         withCredentials: false,
        }).then((res)=>{
        //请求成功的回调函数
        console.log(res)
      }).catch((err)=>{
        //请求失败的回调函数
        console.log(err)
      })
   }
  }
}
</script>
