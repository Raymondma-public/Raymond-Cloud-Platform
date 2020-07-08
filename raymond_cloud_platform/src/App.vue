<template>
  <div id="app">
    
    <a-layout id="components-layout-demo-custom-trigger" style="min-height: 100vh">

    <SideNav ref="sideNav"/>
    <a-layout>
      <a-layout-header style="background: #fff; padding: 0">
<a-row type="flex">

        <a-col :span="6" >
         <a-icon
          class="trigger"
          :type="collapsed ? 'menu-unfold' : 'menu-fold'"
          @click="() => this.$refs.sideNav.toggleCollapse()"
        />
        </a-col>
        <a-col :span="18" >
        <div  style="float: right;">
           <a><a-icon type="code" :style="{ fontSize: '24px', margin: '15px'}"/></a>
        </div>
        </a-col>
</a-row>
      
      </a-layout-header>
      <a-layout-content
        :style="{ margin: '24px 16px', padding: '24px', background: '#fff', minHeight: '280px' }"
      >
        <router-view/>
      </a-layout-content>
    <Footer/>
    </a-layout>
  </a-layout>

  </div>






</template>

<script>
import SideNav from './components/SideNav';
import Footer from './components/Footer';

export default {
  name: 'App',
   data() {
    return {
      collapsed: false
    };
  },
  components:{
    SideNav,
    Footer
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  height: 100vh;
  /* margin-top: 60px; */
}
/* #components-layout-demo-fixed-sider .logo {
  height: 32px;
  background: rgba(255, 255, 255, 0.2);
  margin: 16px;
} */
#components-layout-demo-custom-trigger .trigger {
  font-size: 18px;
  line-height: 64px;
  padding: 0 24px;
  cursor: pointer;
  transition: color 0.3s;
}

#components-layout-demo-custom-trigger .trigger:hover {
  color: #1890ff;
}

</style>
