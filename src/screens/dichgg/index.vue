<template>
  <nb-container :style="{ backgroundColor: '#fff' }">
    <nb-header>
      <nb-left>
        <nb-button transparent :onPress="Goback">
          <nb-icon name="arrow-back" />
        </nb-button>
      </nb-left>
      <nb-body>
        <nb-title>Google Dịch</nb-title>
      </nb-body>
      <nb-right />
    </nb-header>
    <web-view ref="WEBVIEW_REF" :source="{uri: 'https://translate.google.com/?hl=vi'}" />
    <view class="view-wrapper-1">
      <nb-button rounded warning :onPress="ToScreenD">
        <nb-text>Dịch Hán Việt</nb-text>
      </nb-button>
      <nb-button rounded warning :onPress="ToScreenI">
        <nb-text>Lấy text từ Hình ảnh</nb-text>
      </nb-button>
    </view>
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
    },
    ToScreenD() {
      this.navigation.navigate("Dich");
    },
    ToScreenI() {
      this.navigation.navigate("DichImg");
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