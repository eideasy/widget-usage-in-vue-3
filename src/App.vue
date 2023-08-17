<script setup>
import EideasyWidget from '@/EideasyWidget.vue';

const clientId = "ak7lGUHjoK2Cam2Nr9yTDpu3SOPttYFx";
const docId = "uMv8cfU4DTrIlCCri5R11SmaGiLfeL2Lz493gSyD";

function onSuccess(data) {
  console.log('!!!!!! success !!!!!!!');
  console.log(data);
}

function onFail(error) {
  console.log('!!!!!! fail !!!!!!!');
  console.log(error);
}
</script>

<template>
  <div>
    <EideasyWidget
      :client-id="clientId"
      :doc-id="docId"
      :on-success="onSuccess"
      :on-fail="onFail"
    />
  </div>

</template>

<style scoped>

</style>
