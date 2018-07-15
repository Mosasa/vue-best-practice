<template>
  <div id="wrapper">
    <p>
      FullName: {{fullName}}
    </p>
    <p>
      FirstName: <input type="text" v-model="firstName">
    </p>
    <p>obj.a {{obj.a}}</p>
    <p>obj.a <input type="text" v-model="obj.a"></p>
    <main-component></main-component>
    <nav class="navbar navbar-default">
      <div class="container">
        <a href="" class="navbar-brand">
          <i class="glyphicon glyphicon-time"></i>
          计划板
        </a>
        <ul class="nav navbar-nav">
          <li>
            <router-link to="/home">首页</router-link>
          </li>
          <li>
            <router-link to="/time-entries">计划列表</router-link>
          </li>
        </ul>
      </div>
    </nav>
    <div class="container">
      <div class="col-sm-3">
        <sidebar></sidebar>
      </div>
      <div class="col-sm-9">
        <router-view/>
      </div>
    </div>
    <!-- <img src="./assets/logo.png"> -->
    <!-- <router-view/> -->
  </div>
</template>

<script>
import mainComponent from '@/components/mainComponent'
import Sidebar from '@/components/Sidebar'
export default {
  name: 'App',
  data() {
    return {
      firstName: '凯',
      lastName: '曾',
      fullName: '',
      obj: {
        a: 123
      }
    }
  },
  watch: {
    obj: {
      handler (newName, oldName) {
        console.log('obj.a changed');
      },
      immediate: true,
      deep: true //监听的对象是有深度的，监听obj下的a
    },
    firstName: {
      handler(newName, oldName){//handler 定义当数据改变由谁处理
        this.fullName = newName + '' +this.lastName      
      },
      immediate: true
    }
    // firstName (newName, oldName) {
    //   console.log(newName, oldName)
    // }
  },
  // computed: {
  //   fullName() {
  //     return `${this.firstName} ${this.lastName}`
  //   }
  // },
  components: {
     mainComponent,
    'sidebar': Sidebar
  }
}
</script>

<style>

</style>
