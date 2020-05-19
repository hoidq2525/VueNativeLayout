<template>
  <nb-container :style="{ backgroundColor: '#fff' }">
    <nb-header>
      <nb-left>
        <nb-button transparent :onPress="() => this.props.navigation.openDrawer()">
          <nb-icon name="arrow-back" />
        </nb-button>
      </nb-left>
      <nb-body>
        <nb-title>Dịch Text Hán Việt</nb-title>
        <!-- <nb-title>Dịch Chữ Hán</nb-title> -->
      </nb-body>
      <nb-right />
    </nb-header>
    <nb-content padder>
      <nb-text>Nhập chữ Hán</nb-text>
      <nb-textarea
        v-model="text"
        class="text-area"
        :rowSpan="10"
        bordered
        placeholder="Nhập text muốn dịch vào đây"
      />
      <nb-text>Kết quả</nb-text>
      <nb-textarea v-model="text2" class="text-area" :rowSpan="18" bordered />

      <view class="view-wrapper-1">
        <nb-button rounded success :style="stylesObj" :onPress="onPressPhare">
          <nb-text>Dịch Phare</nb-text>
        </nb-button>
        <nb-button rounded warning :style="stylesObj" :onPress="onPressHanViet">
          <nb-text>Hán Việt</nb-text>
        </nb-button>
        <nb-button rounded warning :style="stylesObj" :onPress="TransleEng">
          <nb-text>Google Dịch</nb-text>
        </nb-button>
        <nb-button rounded danger :style="stylesObj" :onPress="onPressEmpty">
          <nb-text>Xóa</nb-text>
        </nb-button>
      </view>
    </nb-content>
  </nb-container>
</template>

<script>
import axios from "axios";
import { Toast } from "native-base";
import { WebView } from "react-native-webview";
export default {
  props: {
    navigation: {
      type: Object
    }
  },
  data() {
    return {
      text: "先秦兩漢先秦兩漢先秦兩漢先秦兩漢先秦兩漢先秦兩漢",
      text2: "",
      stylesObj: {
        marginTop: 10
      },
      istext: false
    };
  },
  methods: {
    htmlrender() {
      let str = `<p>fsdfsdf</p>`;
      return str;
    },
    onPressEmpty() {
      this.text = "";
      this.text2 = "";
      Toast.show({
        text: "Xóa văn bản thành công!",
        type: "success",
        position: "top"
      });
    },
    TransleEng() {
      this.navigation.navigate("DichGG");
    },
    onPressPhare() {
      let url = "http://www.vietphrase.info/Vietphrase/TranslateVietPhraseS";
      this.CallAPi(url);
    },
    onPressHanViet() {
      let url = "http://www.vietphrase.info/Vietphrase/TranslateHanViet";
      this.CallAPi(url);
    },
    CallAPi(url) {
      axios
        .post(url, {
          chineseContent: this.text
        })
        .then(response => {
          this.text2 = response.data;
        })
        .catch(err => {
          console.log(err);
        });
    }
  },
  components: {
    "web-view": WebView
  }
};
</script>

<style>
.view-wrapper-1 {
  flex-direction: row;
  justify-content: space-between;
}
.text-area {
  background-color: antiquewhite;
  padding: 10px;
  color: rgb(8, 8, 8);
  text-transform: capitalize;
  border-radius: 5px;
}
</style>