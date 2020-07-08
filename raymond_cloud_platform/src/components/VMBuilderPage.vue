<template>
  <div>
    <a-row type="flex">
       <a-col :span="6" >
   vmCode<a-input id="vmCode" type="text" name="vmCode" v-model="vmCode"></a-input>
   </a-col >
   </a-row >

    <a-row type="flex">
       <a-col :span="12" >
   
   dockerBuildString<a-textarea id="dockerBuildString" type="text" name="dockerBuildString" rows="10"
                           cols="60" v-model="dockerBuildString"></a-textarea>
                           </a-col >
   </a-row >

  <a-row type="flex">
       <a-col :span="12" >
k8sConfig<a-textarea id="k8sConfig" type="text" name="k8sConfig" rows="10" cols="60"  v-model="k8sConfig"></a-textarea>
                           </a-col >
   </a-row >
<!-- <a-input id="token" type="hidden" name="token" value="1"></a-input><br/> -->
 <a-row type="flex">
<a-button type="primary" v-on:click="getVMConfig">getVMConfig</a-button>
<a-button type="primary" v-on:click="buildVM">build VM</a-button>
   </a-row >
<!-- <button id="getVMConfig">getVMConfig</button>
<button id="buildVM">build VM</button> -->
<!-- <br/>
#dockerBuild===================<br/>
<div id="dockerBuildText" style="white-space: pre-wrap;"></div>
<br/>

#k8s config===================<br/>
<div id="k8sConfigText" style="white-space: pre-wrap;"></div> -->
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      token: 1,
      vmCode: "",
      dockerBuildString: "",
      k8sConfig: "",
    
    }
  },
  methods:{
     getVMConfig (event) {
        this.token=1;

        let data = {token:this.token,vmCode: this.vmCode};
        axios.get('http://192.168.1.240:30084/getVMConfig', { params: data })
    .then((res) => { console.table(res.data) 
        if(res.data.obj!=null){
        this.dockerBuildString=res.data.obj.dockerBuildString
        this.k8sConfig=res.data.obj.k8sConfig
        }

        this.$notification.open({
          message: res.data.message,
          description:
            res.data.message,
          onClick: () => {
            console.log('Notification Clicked!');
          },
        });
    
    }).catch((error) => { console.error(error) })
    .finally(() => { /* 不論失敗成功皆會執行 */ })
    },
    buildVM (event) {
       let data = {token:this.token,vmCode: this.vmCode,dockerBuildString:this.dockerBuildString,k8sConfig:this.k8sConfig};


       const formData = new FormData()
      Object.keys(data).forEach(key => {
        formData.append(key, data[key])
      })
        axios.post('http://192.168.1.240:30084/buildVM', formData)
      .then((res) => { 
        let data=res.data
        console.table(data.message) 
      this.$notification.open({
        message: data.message,
        description:
          data.message,
        onClick: () => {
          console.log('Notification Clicked!');
        },
      });
      }
      
      ).catch((error) => { console.error(error) })
    .finally(() => { /* 不論失敗成功皆會執行 */ })
    
    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
