<template>
<!-- to="#end-of-body"，to后是id -->
<!-- 查看控制台的元素，下面这两个(div/teleport两个标签)的顺序要看public/index.html的<div id="end-of-body"></div>是在<div id="app"></div>前还是后 -->
  <!-- <div>This should be at the top</div>
  <teleport to="#end-of-body" :disabled="!toggle">hello teleport to end of body</teleport> -->

<!-- teleport可以保存dom节点的状态: 当点击的时候视频会在上面，再点击的时候视频会在下面，当不停切换，视频一直在播放 -->
 <teleport to="#end-of-body" :disabled="!toggle">
   <!-- 视频播放无效 -->
   <video controls autoplay="true" loop="true" width="600">
   <source src="https://vd4.bdstatic.com/mda-kedja19a18h7eass/hd/mda-kedja19a18h7eass.mp4?v_from_s=hkapp-haokan-hna&auth_key=1642864605-0-0-51398c465a72335b4847c819449912c5&bcevod_channel=searchbox_feed&pd=1&pt=3&logid=2805773478&vid=4090861954793250282&abtest=&klogid=2805773478" type="video/mp4">
</video>
 </teleport>
 <div>toggle value:{{toggle}}</div>
 <div>This should be at the top</div>
  <button type="button" @click="toggleHandle">toggle</button>
</template>

<!--------------------------------------------------------------------------------------------------------------------------------------->

<!-- 顺序问题：disabled为true的话，#end-of-body这个id就生效，为false就在id="app"里，为true就在id="end-of-body"里 -->
 <!-- <teleport to="#end-of-body" :disabled="!toggle">hello teleport to end of body</teleport>
 <div>toggle value:{{toggle}}</div>
 <div>This should be at the top</div>
  <button type="button" @click="toggleHandle">toggle</button>
</template> -->

<script>
import { ref } from 'vue'
export default {
  name: 'App',
  setup(){
    const toggle=ref(false)
    const toggleHandle=()=>{
      toggle.value=!toggle.value
    }
    return{
      toggle,
      toggleHandle
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
