<template>
  <img class="logo" src="../assets/resto-logo.jpg" /> <br />
  
  <div class="register">
    <h1>Signup</h1>
    <input type="text" v-model="name" placeholder="Enter Name" />
    <input type="text" v-model="email" placeholder="Enter Email" />
    <input type="password" v-model="password" placeholder="Enter Password" />
    <button v-on:click="signUp">Signup</button>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "SignUp",
  data() {
    return {
      name: "",
      email: "",
      password: "",
    };
  },
  methods: {
    async signUp() {
      console.warn("signUp", this.name, this.email, this.password);
      let result = await axios.post("http://localhost:3000/users", {
        name: this.name,
        email: this.email,
        password: this.password,
      });
      console.warn(result);
      if (result.status == 201) {
        alert("Signup Done");
      }
      localStorage.setItem("user-info", JSON.stringify(result.data));
    },
  },
};
</script>

<style>

.head{


}
.logo {
  display: flex;
  justify-content: center;  
  align-items: center;
  width: 150px;
  margin-left: auto;
  margin-right: auto;
}


.register input {
  
  width: 300px;
  height: 40px;
  padding-left: 20px;
  display: block;
  margin-bottom: 30px;
  margin-left: auto;
  margin-right: auto;
  border: 1px solid skyblue;
}

.register button {
  width: 300px;
  height: 40px;
  color: white;
  background-color: skyblue;
  border: 1px solid skyblue;
  cursor: pointer;
}
</style>
