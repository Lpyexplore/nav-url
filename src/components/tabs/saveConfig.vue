<template>
  <div class="save-config-container" v-show="isShowSaveAlert">
    <div class="save-config-alert">
      <div class="close-save-config-alert" @click="handleSaveConfigAlert(false)"></div>
      <div class="save-config-alert-title">保存配置</div>
      <div class="save-config-alert-remind">说明：保存下载成功后会生成一个json文件，请注意保存，方便之后一键导入</div>
      <lp-button type="primary" class="save-config-btn" @_click="saveConfig">Save</lp-button>
    </div>
  </div>
</template>

<script>
/* 组件 */
import lpButton from '@/components/public/lp-button/lp-button'
/* 功能模块 */
import saveConfigFunction from '@/use/saveConfig'
export default {

    components: {
        lpButton
    },
    setup() {

        let { isShowSaveAlert, handleSaveConfigAlert, saveConfig } = saveConfigFunction()

        return { isShowSaveAlert, saveConfig, handleSaveConfigAlert }
    }
}
</script>

<style scoped>
.save-config-container{
  position: fixed;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  background-color: rgba(0, 0, 0, .2);
  z-index: 999;
}
.save-config-alert{
  position: absolute;
  top: 45%;
  left: 50%;
  width: 300px;
  height: 200px;
  transform: translate(-50%, -50%);
  background-color: white;
  border-radius: 10px;
  box-shadow: 0 0 5px rgba(0, 0, 0, .2);
}
.close-save-config-alert{
  position: relative;
  height: 30px;
}
.close-save-config-alert::before{
  content: '\2716';
  position: absolute;
  right: 10px;
  top: 5px;
  cursor: pointer;
}
.save-config-alert-title{
  height: 30px;
  text-align: center;
  line-height: 30px;
  font-size: 17px;
  font-weight: 600;
}
.save-config-alert-remind{
  font-size: 13px;
  color: rgb(153, 145, 145);
  padding: 5px 20px;
  height: 30px;
}
.save-config-btn{
  height: 40px;
  width: 100px;
  margin: 20px auto;
  display: block;
}
</style>