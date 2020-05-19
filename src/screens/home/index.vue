<template>
  <nb-container :style="{ backgroundColor: '#fff' }">
    <nb-header>
      <nb-left>
        <nb-button transparent :onPress="backWeb">
          <nb-icon name="arrow-back" />
        </nb-button>
      </nb-left>
      <nb-body>
        <nb-title>Trang Web</nb-title>
      </nb-body>
      <nb-right />
    </nb-header>
    <web-view  ref="WEBVIEW_REF" :source="{uri: 'https://trickgame24h.blogspot.com'}" />
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
    backWeb() {
      this.$refs.WEBVIEW_REF.goBack();
    }
  },
  components: {
    "web-view": WebView
  }
};
</script>

<style>
.view-wrapper-1 {
  justify-content: center;
  align-items: center;
  flex-direction: row;
  padding-bottom: 20px;
  /* justify-content: space-between; */
}
</style>