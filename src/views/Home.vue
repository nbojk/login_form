<template>
  <div class="home">
    <div class="background">
      <div class="left">
        <div class="text">
        <h3>Login</h3>
        <p>By logging in you agree to the ridiculously long terms that you didn't bother to read.</p>
        </div>
      </div>
      <div class="right">
        <div class="loginForm">
        <label for="email">Email</label>
        <input id="email" v-model="inputEmail" type="text">
        <label for="pass">Password</label>
        <img class="showHide" src="../assets/eye-blocked.svg" v-on:click="changeVisibility">
        <input id="pass" v-model="inputPass" v-bind:type="visible">
        <div v-if="hasError">{{ error }}</div>
        <button class="logbtn" v-on:click="validate">Log in</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  data: function() {
    return {
      email: "nev@nev.com",
      pass: "secret",
      inputEmail: "",
      inputPass: "",
      visible: "password",
      error: "The credentials are not correct",
      hasError: false
    }
  },
  methods: {
    changeVisibility: function() {
      if (this.visible === "password") {
        this.visible = "text";
      } else {
        this.visible = "password";
      }
    },
    validate: function() {
      if (this.inputEmail === this.email && this.inputPass === this.pass) {
        this.$router.push({path: '/about'});
      } else {
        this.hasError = true;
      }
    }
  }
}
</script>

<style lang="scss">

  .background {
    background-color: #dfe0e3;
    width: 800px;
    height: 400px;
    position: relative;
    margin: 0 auto;
    

    .left {
      width: 300px;
      height: 150px;
      background-color: #fff;
      position: absolute;
      top: 120px;
      left: 155px;
      .text {
        width: 200px;
        height: 75px;
        background-color: #fff;
        text-align: left;
        padding-left: 40px;
        h3 {
          font-family: Arial, Helvetica, sans-serif;
          font-size: 30px;
          padding: 20px 0 0 0;
          margin: 0;
        }
        p {
          color: #dfe0e3;
          font-family: Arial, Helvetica, sans-serif;
          font-size: 14px;
        }
      }
    }
    .right {
      width: 240px;
      height: 200px;
      background-color: #32475c;
      position: absolute;
      top: 93px;
      left: 406px;
      border-radius: 5px;
      box-shadow: 5px 10px 11px 5px #a8a5a5;
      }
      .loginForm {
        width: 160px;
        height: 100px;
        text-align: left;
        align-items: left;
        padding: 35px 10px 10px 30px;
        input {
          display: block;
          background-color: #32475c;
          border: 1px solid #344b61;
          color: #9b9b9b;
          &:focus {
            outline: none;
          } 
        }
        label {
          color: #9b9b9b;
          font-family: Arial, Helvetica, sans-serif;
          font-size: 12px; 
        }
        #email {
          margin-bottom: 15px;
        }
        .showHide {
          padding-left: 7px;
          width: 20px;
          height: 20px;
        }
        .logbtn {
          width: 100%;
          height: 30px;
          margin-top: 20px;
          color: rgb(92, 92, 92);
          font-size: 13px;
        
      }
      
    }
  }

</style>
