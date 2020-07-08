<template>
        <div id="terminalFrame"  v-on:click="toggle">
          <div>
            Terminal
          </div>
        <iframe id="myIframe" :src="src" ref="iframe" v-if="display"></iframe>
        </div>
</template>
<script>
export default {
  data() {
    return {
      src: 'http://192.168.1.240:30022/',
      display:false
    };
  },
  watch: {

  },
  methods: {
    toggle(e){
      this.display=!this.display;
    }


  },mounted(){
            /**
             * iframe-宽高自适应显示   
             */
            // const oIframe = document.getElementById('bdIframe');
            // const deviceWidth = document.documentElement.clientWidth;
            // const deviceHeight = document.documentElement.clientHeight;
            // oIframe.style.width = (Number(deviceWidth)-220) + 'px'; //数字是页面布局宽度差值
            // oIframe.style.height = (Number(deviceHeight)-120) + 'px'; //数字是页面布局高度差
        },
};
</script>
<style >
#terminalFrame {
  background: aliceblue;
  position: fixed;
  width: 100%;
  left:0;
  bottom:0;
  /* top: 100%;
 transform: translateY(-100%); */
}

#myIframe{
  height: 300px;
  width: 100%;
  resize: both;
}
</style>