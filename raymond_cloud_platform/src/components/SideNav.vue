<template>
  <a-layout-sider v-model="collapsed" :trigger="null" collapsible>
    <div class="logo" :style="{ fontSize: '42px', color: '#08c' }">
      <a-icon type="code" />
      <span v-if="collapsed == false">RCP</span>
    </div>

    <a-menu theme="dark" mode="inline" :default-selected-keys="['1']">
      <a-menu-item key="1">
        <router-link to="/">
          <a-icon type="user" />
          <span>Home</span>
        </router-link>
      </a-menu-item>
      <a-menu-item key="2">
        <router-link to="/vm-builder">
          <a-icon type="video-camera" />
          <span>VM Builder</span>
        </router-link>
      </a-menu-item>
      <a-menu-item key="3">
        <a-icon type="upload" />
        <span>nav 3</span>
      </a-menu-item>
    </a-menu>
  </a-layout-sider>
</template>
<script>
export default {
  data() {
    return {
      current: ["mail"],
      openKeys: ["sub1"],
      collapsed: false
    };
  },
  watch: {
    openKeys(val) {
      console.log("openKeys", val);
    }
  },
  methods: {
    toggleCollapse() {
      this.collapsed = !this.collapsed;
    },
    handleClick(e) {
      console.log("click", e);
    },
    titleClick(e) {
      console.log("titleClick", e);
    }
  }
};
</script>
<style>
#components-layout-demo-custom-trigger .logo {
  height: 32px;
  /* background: rgba(255, 255, 255, 0.2); */
  margin: 24px;
  color: aliceblue;
}
</style>
