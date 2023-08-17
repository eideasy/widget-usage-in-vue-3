<script setup>
import '@eid-easy/eideasy-widget';
import {ref, onMounted, onUpdated} from 'vue';

const props = defineProps({
  clientId: String,
  docId: String,
  onSuccess: Function,
  onFail: Function,
})

const widgetHolder = ref(null);
function renderWidget() {
  const eidEasyWidget = document.createElement('eideasy-widget');

  const settings = {
    countryCode: 'EE', // ISO 3166  two letter country code
    language: 'en', // ISO 639-1 two letter language code,
    sandbox: true,
    clientId: props.clientId,
    docId: props.docId,
    enabledMethods: {
      signature: 'all',
      // if you want to enable specific methods, then use
      // signature: ['ee-id-login', 'lv-id-login'],
    },
    selectedMethod: null,
    enabledCountries: 'all',
    onSuccess: function (data) {
      props.onSuccess(data);
    },
    onFail: function (error) {
      props.onFail(error);
    },
  }

  Object.keys(settings).forEach(key => {
    eidEasyWidget[key] = settings[key];
  });

  widgetHolder.value.innerHTML = '';
  widgetHolder.value.appendChild(eidEasyWidget);
}

onUpdated(() => {
  // text content should be the same as current `count.value`
  console.log('UPDATED');
  renderWidget();
});

onMounted(() => {
  // text content should be the same as current `count.value`
  console.log('MOUNTED');
  renderWidget();
});
</script>

<template>
  <div ref="widgetHolder"/>
</template>
