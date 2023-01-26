<template>
  <div class="wrapper">
    <side-bar :title="'Fate/GO 茹西教王的理想鄉'">
      <template slot="links">
        <sidebar-link
          to="/dashboard"
          name="首頁"
          color="#9D7D5C"
          style="color: #9d7d5c !important"
          class="slier Siderdashboard"
        />
        <a href="https://www.facebook.com/472978160149131/" name="FaceBook" class="slier SiderFaceBook href" >FaceBook</a>
        <a href="https://discord.gg/nEaXVvS"  class="slier SiderFaceBook href" >Discord</a>
        <sidebar-link to="/Servant" name="從者" class="slier SiderServant" />
        <sidebar-link to="#" name="技能" class="slier SiderCommon" />
        <sidebar-link to="#" name="寶具" class="slier SiderCommon" />
        <sidebar-link to="#" name="HP與ATK" class="slier SiderCommon" />
        <sidebar-link to="#" name="隱藏數値" class="slier SiderCommon" />
        <sidebar-link to="#" name="概念禮裝" class="slier Sidercraft_essence" />
        <sidebar-link to="#" name="指令紋章" class="slier Sidercode" />
        <sidebar-link to="#" name="素材道具" class="slier Siderdrop" />
        <sidebar-link to="#" name="關卡" class="slier Siderquest" />
        <sidebar-link to="#" name="御主相關" class="slier Siderequio" />
        <sidebar-link to="#" name="贊助支持" class="slier Siderdonate" />
        <sidebar-link to="#" name="意見回饋" class="slier Siderbanner" />
        <sidebar-link to="#" name="意見回饋" class="slier Siderbanner" />
        <sidebar-link to="#" name="過去活動" class="slier SiderEvent" />
        <div>
          <img class="pa-2" :src="require(`@/assets/image${img}`)" alt="" v-for="(img,index) in imglist" :key="index" />
        </div>
        <!-- <sidebar-link to="/icons" :name="$t('sidebar.icons')" icon="tim-icons icon-atom"/>
        <sidebar-link to="/maps" :name="$t('sidebar.maps')" icon="tim-icons icon-pin"/>
        <sidebar-link to="/notifications" :name="$t('sidebar.notifications')" icon="tim-icons icon-bell-55"/>
        <sidebar-link to="/profile" :name="$t('sidebar.userProfile')" icon="tim-icons icon-single-02"/>
        <sidebar-link to="/table-list" :name="$t('sidebar.tableList')" icon="tim-icons icon-puzzle-10"/>
        <sidebar-link to="/typography" :name="$t('sidebar.typography')" icon="tim-icons icon-align-center"/>
        <sidebar-link to="/dashboard?enableRTL=true" :name="$t('sidebar.rtlSupport')" icon="tim-icons icon-world"/> -->
      </template>
    </side-bar>

    <div class="main-panel">
      <top-navbar></top-navbar>

      <dashboard-content @click.native="toggleSidebar"> </dashboard-content>

      <content-footer></content-footer>
    </div>
  </div>
</template>
<style lang="scss"></style>
<script>
import TopNavbar from "./TopNavbar.vue";
import ContentFooter from "./ContentFooter.vue";
import DashboardContent from "./Content.vue";
import MobileMenu from "./MobileMenu";
export default {
  data:()=> {
    return{
      imglist:[
        "/2023/newyear2023_cp_imsac/top_banner02.png",
        "/2023/newyear2023_pu_elswg/top_banner.png",
        "/2023/luckybag2023_edhgc/top_banner.png",
        "/2022/nahui-mictlan_full_aezqu/top_banner_02.png",
        "/2022/1201info_eqlsr/top_banner.png",
      ]
    }
  },
  components: {
    TopNavbar,
    ContentFooter,
    DashboardContent,
    MobileMenu,
  },
  methods: {
    toggleSidebar() {
      if (this.$sidebar.showSidebar) {
        this.$sidebar.displaySidebar(false);
      }
    },
  },
};
</script>

<style scoped>
.sidebar {
  background-image: url("~@/assets/image/bg.jpg") !important;
  background-repeat: repeat !important;
  background-size: 30px 30px !important;
}
.pa-2{
  padding: 8px !important;
}

.slier {
  padding-left: 60px;
  padding-bottom: 10px;
  margin-bottom: 5px;
  display: flex;
  align-items: center;
  margin: 10px
}

.href {
  color: #9d7d5c !important;
  padding-left: 84px;
  font-weight: 600
}

.Siderdashboard {
  background-image: url("~@/assets/image/icon/siderbar/sidebar01.png");
  background-size: cover;
  height: 60px;
}

.SiderFaceBook {
  background-image: url("~@/assets/image/icon/siderbar/sidebar17.png");
  background-size: cover;
  height: 60px;
}

.SiderServant {
  background-image: url("~@/assets/image/icon/siderbar/sidebar05.png");
  background-size: cover;
  height: 60px;
}
.SiderCommon {
  background-image: url("~@/assets/image/icon/siderbar/sidebar00.png");
  background-size: cover;
  height: 42px;
  margin-left: 35px;
}
.Sidercraft_essence {
  background-image: url("~@/assets/image/icon/siderbar/sidebar09.png");
  background-size: cover;
  height: 60px;
}
.Sidercode {
  background-image: url("~@/assets/image/icon/siderbar/sidebar18.png");
  background-size: cover;
  height: 60px;
}

.Sidercode {
  background-image: url("~@/assets/image/icon/siderbar/sidebar18.png");
  background-size: cover;
  height: 60px;
}
.Siderdrop {
  background-image: url("~@/assets/image/icon/siderbar/sidebar15.png");
  background-size: cover;
  height: 60px;
}
.Siderquest {
  background-image: url("~@/assets/image/icon/siderbar/sidebar04.png");
  background-size: cover;
  height: 60px;
}
.Siderequio {
  background-image: url("~@/assets/image/icon/siderbar/sidebar03.png");
  background-size: cover;
  height: 60px;
}
.Siderdonate {
  background-image: url("~@/assets/image/icon/siderbar/sidebar11.png");
  background-size: cover;
  height: 60px;
}
.Siderbanner {
  background-image: url("~@/assets/image/icon/siderbar/sidebar08.png");
  background-size: cover;
  height: 60px;
}
.SiderEvent {
  background-image: url("~@/assets/image/icon/siderbar/sidebar10.png");
  background-size: cover;
  height: 60px;
}
</style>
