<template>
  <nb-container :style="{ backgroundColor: '#fff' }">
    <nb-header>
      <nb-left>
        <nb-button transparent :onPress="Goback">
          <nb-icon name="arrow-back" />
        </nb-button>
      </nb-left>
      <nb-body>
        <nb-title>Img Sang Text</nb-title>
      </nb-body>
      <nb-right />
    </nb-header>
    <web-view
      ref="WEBVIEW_REF"
      :source="{uri: 'http://preview.codecanyon.net/item/pic-to-txt-turn-images-into-editable-text-optical-character-recognition-ocr/full_screen_preview/22809285'}"
    />
    <!-- <web-view :source="{uri: 'http://195.148.30.97/cgi-bin/ocr.py'}" /> -->
  </nb-container>
</template>

<script>
import { WebView } from "react-native-webview";
export default {
  props: {
    navigation: {
      type: Object
    }
  },
  data() {
    return {
      text2: ""
    };
  },
  methods: {
    Goback() {
      this.$refs.WEBVIEW_REF.goBack();
    }
  },
  components: {
    "web-view": WebView
  }
};
</script>

<style>
</style>