<template>
  <root>
    <app-navigation></app-navigation>
  </root>
</template>

<script>
import {
  createAppContainer,
  createStackNavigator,
  createDrawerNavigator
} from "vue-native-router";
import { Root } from "native-base";
import HomeScreen from "./screens/home/index.vue";
import DichGoogle from "./screens/dichgg/index.vue";
import DichScreen from "./screens/dich/index.vue";
import DichImgScreen from "./screens/dichImg/index.vue";
import SideBarScreen from "./screens/sidebar/index.vue";

const Drawer = createDrawerNavigator(
  {
    Home: { screen: HomeScreen },
    Dich: { screen: DichScreen },
    DichImg: { screen: DichImgScreen },
    DichGG: { screen: DichGoogle }
  },
  {
    initialRouteName: "Dich",
    contentOptions: {
      activeTintColor: "#e91e63"
    },
    contentComponent: SideBarScreen
  }
);

const AppNavigation = createAppContainer(
  createStackNavigator(
    {
      Drawer: { screen: Drawer }
    },
    {
      initialRouteName: "Drawer",
      headerMode: "none"
    }
  )
);
export default {
  components: { Root, AppNavigation }
};
</script>
