<template>
  <div class="row">
    <div class="col-12">
      <card type="chart">
        <!-- <div class="d-flex">
            <div class="squeree">◆</div>
            <div>選擇職階</div>
            <div class="squeree">◆</div>
            <div>
            </div>
          </div> -->

        <div class="d-flex col-12" style="color:white">
          <div
            class="col-lg-3 col-md-3 col-sm-12 pa-0 imgborder d-flex align-center justify-center"
          >
            <!-- show-arrows-on-hover -->
            <!-- :show-arrows="false" -->
            <!-- cycle
              interval="3000" -->
            <v-carousel
              height="200px"
              hide-delimiter-background

            >
              <template v-slot:prev="{ on, attrs }">
                <div v-on="on" class="arrow_left">
                  <v-btn fab>
                    <img :src="require(`@/assets/image/left_btn.png`)" alt="" width="40px">
                  </v-btn>
                </div>
                <!-- <v-btn color="success" v-bind="attrs" v-on="on"
                  >PREV @Bulchsu</v-btn
                > -->
              </template>
              <template v-slot:next="{ on, attrs }">
                <div v-on="on" class="arrow_right">
                  <v-btn fab>
                    <img :src="require(`@/assets/image/right_btn.png`)" alt="" width="40px">
                  </v-btn>
                </div>
              </template>
              <v-carousel-item
                v-for="(item, i) in items"
                :key="i"
                reverse-transition="fade-transition"
                transition="fade-transition"
              >
                <div class="d-flex align-center justify-center">
                  <img :src="item.src" height="200px" />
                  <!-- <img :src="require(`@/assets/image/Servants/Status/1001500/status_servant_2.png`)" /> -->
                </div>
              </v-carousel-item>
            </v-carousel>
            <!-- <img src="@/assets/image/icon/faces/10015000.png" /> -->
          </div>
          <div class="col-lg-9 col-md-9 col-sm-12 pa-0">
            <div class="d-flex col-12 pa-0">
              <div class="tdhead col-2 pa-0">編號</div>
              <div class="tdhead col-2 pa-0">星數</div>
              <div class="tdhead col-4 pa-0">名稱</div>
              <div class="tdhead col-2 pa-0">職階</div>
              <div class="tdhead col-2 pa-0">分類</div>
            </div>
            <div class="d-flex col-12 pa-0">
              <div class="tdbody d-flex col-2 pa-0 align-center justify-center">
                No.369
              </div>
              <div class="tdbody d-flex col-2 pa-0 align-center justify-center">
                <div v-for="(star, index) in 5" :key="index" class="star">
                  ★
                </div>
              </div>
              <div class="tdbody col-4 pa-0 d-flex align-center justify-center">
                <div class="jpname">コトミネキレイ</div>
                <div class="name">格里戈里・拉斯普丁</div>
              </div>
              <div class="tdbody col-2 pa-0 d-flex align-center justify-center">
                <img
                  :src="require(`@/assets/image/icon/class/class_10_5.png`)"
                  width="60px"
                />
              </div>
              <div class="tdbody col-2 pa-0 d-flex align-center justify-center">
                地
              </div>
            </div>
            <div class="d-flex col-12 pa-0">
              <div class="tdhead col-2 pa-0">HP</div>
              <div class="tdhead col-2 pa-0">ATK</div>
              <div class="tdhead col-2 pa-0">繪師</div>
              <div class="tdhead col-2 pa-0">CV</div>
              <div class="tdhead col-2 pa-0">屬性</div>
              <div class="tdhead col-2 pa-0">性別</div>
            </div>
            <div class="d-flex col-12 pa-0">
              <div class="tdbody d-flex col-2 pa-0 align-center justify-center">
                2069 / 14107
              </div>
              <div class="tdbody d-flex col-2 pa-0 align-center justify-center">
                1716 / 11107
              </div>
              <div class="tdbody col-2 pa-0 d-flex align-center justify-center">
                武内崇
              </div>
              <div class="tdbody col-2 pa-0 d-flex align-center justify-center">
                中田譲治
              </div>
              <div class="tdbody col-2 pa-0 d-flex align-center justify-center">
                秩序・惡
              </div>
              <div class="tdbody col-2 pa-0 d-flex align-center justify-center">
                男性
              </div>
            </div>
            <div class="d-flex col-12 pa-0 ">
              <div class="d-flex col-3 pa-0">
                <div class="tdhead col-12 pa-0">特性</div>
              </div>
              <div class="d-flex col-9 pa-0">
                <div
                  class="tdbody d-flex col-12 pa-0 align-center justify-center"
                >
                  〔男性〕,『地』之力,『秩序』屬性,『惡』屬性,〔從者〕,〔人型〕,〔從者(被EA特攻)〕,〔有天或地之力從者〕,〔龍〕,〔人科從者〕
                </div>
              </div>
            </div>
          </div>
        </div>
      </card>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          // file:///D:/ezio/fgo%20test/fgo-vz/common/images/Servants/Status/1001500/status_servant_1.png
          src: require("@/assets/image/Servants/Status/1001500/status_servant_1.png"),
        },
        {
          src: require("@/assets/image/Servants/Status/1001500/status_servant_2.png"),
        },
        {
          src: require("@/assets/image/Servants/Status/1001500/status_servant_3.png"),
        },
      ],
    };
  },
  methods: {
    getImage(item) {
      return require(item.src);
    },
  },
};
</script>

<style scoped>
.tdhead {
  border-top: 1px solid #666666;
  border-left: 1px solid #666666;
  border-right: 1px solid #666666;
  border-bottom: 1px solid #666666;
  text-align: center;
}
.tdbody {
  border-right: 1px solid #666666;
  border-left: 1px solid #666666;
  border-bottom: 1px solid #666666;
  text-align: center;
}

.imgborder {
  border: 1px solid #666666;
}
.d-flex {
  display: flex;
  flex-wrap: wrap !important;
}
.pa-0 {
  padding: 0px !important;
}
.pa-2 {
  padding: 8px !important;
}
.squeree {
  color: rgb(162, 27, 32);
}
.star {
  color: rgb(255, 213, 0) !important;
  text-shadow: black 1px 1px 1px;
}
.name {
  color: blue;
}
.jpname {
  color: red;
}

.align-center {
  align-content: center;
}
.justify-center {
  justify-content: center;
}

</style>
