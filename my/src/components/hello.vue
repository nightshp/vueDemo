<template>
  <div>
    <div id="vue">{{message}}</div>
    <br />
    <div>
      用户名：
      <input type="text" placeholder="请输入用户名" ref="userName" />
    </div>
    <div>
      密码：
      <input type="password" placeholder="请输入密码" ref="password" />
    </div>
    <button @click="register()">注册</button>
  </div>
</template>

<script>
import api from "../api/getData";
import axios from "axios";
import { fail } from "assert";
import { error } from "util";
export default {
  name: "hello",
  data() {
    return {
      message: "注册界面"
    };
  },
  methods: {
    register() {
      var userName = this.$refs.userName.value;
      var password = this.$refs.password.value;
      var param = { uName: userName, uPassword: password };
      // this.$axios({
      //   url: "http://127.0.0.1:8080/user/register",
      //   method: "post",
      //   data: param,
      //   asay: true,
      //   contentType: "application/json;charset=utf-8"
      // }).then(function(res) {
      //   if (res.ResultCode == 0) {
      //     alert("success");
      //   } else {
      //     alert("fail");
      //   }
      // });
      axios
        .post(api.register, param)
        .then(function(res) {
          if (res.data.message == "插入成功") {
            alert("success");
          } else {
            alert("fail");
          }
        })
        .catch(error => {
          alert("失败", error);
        });
    }
  },
  components: {}
};
</script>

<style>
#vue {
  color: green;
  font-size: 28px;
}
</style>
