<template>
  <div>
    <ccPreloader v-if="this.$store.state.CcPreloader"></ccPreloader>
    <CcMainHeader></CcMainHeader>
    <ccLeftSideBar></ccLeftSideBar>
    <div class="ccMain" :class="leftSideBarOpen?'leftSideBarOpen':'leftSideBarClose'">
        <router-view></router-view>
    </div>
  </div>
</template>

<script>
import CcPreloader from "@components/CcCore/CcPreloader";
import CcMain from "@CcCore/CcMain";
import CcMainHeader from "@components/CcCore/CcMainHeader";
import CcLeftSideBar from "@CcCore/CcLeftSideBar";
import { mapGetters } from 'vuex';
export default {
  name: "layout",
  components: {
    CcPreloader,
    CcMain,
    CcMainHeader,
    CcLeftSideBar
  },
  computed:{
    ...mapGetters([
      "leftSideBarOpen"
    ])
  }
};
</script>

<style lang="scss" scoped>
@import "../../styles/_variables.scss";

.ccMain{
  margin-top: $header-height+20px;
  transition: margin-left .5s
}
.leftSideBarOpen{
  margin-left: $leftSideBar-width;
}
.leftSideBarClose{
  margin-left: 0;
}

</style>
