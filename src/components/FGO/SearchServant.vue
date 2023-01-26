<template>
  <div class="bdgray">
    <div class="d-flex pa-2 justify-center">
      <div class="icon img_allon" @click="allzhijie(1)"></div>
      <div class="icon img_alloff" @click="allzhijie(0)"></div>
      <div class="icon img_starnew" @click="allstar(1)"></div>
      <div class="icon img_starclear" @click="allstar(0)"></div>
    </div>
    <div class="d-flex pa-2 justify-center">
      <div
        class="icon"
        v-for="(zhijie, index) in zhijies"
        :key="index"
        :class="[
          Selectzhijielist.indexOf(zhijie.id) !== -1
            ? `img_${zhijie.value}_on`
            : `img_${zhijie.value}`,
        ]"
        @click="Selectzhijie(zhijie)"
      ></div>
    </div>
    <div class="d-flex pa-2 justify-center">
      <v-btn
        small
        class="star"
        :class="[starlist.indexOf(1) !== -1 ? '' : 'btnstarcancel']"
        @click="setstarlist(1)"
        >★</v-btn
      >
      <v-btn
        small
        class="star"
        :class="[starlist.indexOf(2) !== -1 ? '' : 'btnstarcancel']"
        @click="setstarlist(2)"
        >★★</v-btn
      >
      <v-btn
        small
        class="star"
        :class="[starlist.indexOf(3) !== -1 ? '' : 'btnstarcancel']"
        @click="setstarlist(3)"
        >★★★</v-btn
      >
      <v-btn
        small
        class="star"
        :class="[starlist.indexOf(4) !== -1 ? '' : 'btnstarcancel']"
        @click="setstarlist(4)"
        >★★★★</v-btn
      >
      <v-btn
        small
        class="star"
        :class="[starlist.indexOf(5) !== -1 ? '' : 'btnstarcancel']"
        @click="setstarlist(5)"
        >★★★★★</v-btn
      >
    </div>

    <div class="pa-2">
      <v-data-table
        :headers="tableheader"
        Dense
        :items="showdata"
        sort-by="collectionNo"
        :sort-desc="true"
        :items-per-page="10"
      >
        <template v-slot:item.name="{ item }">
          <a href="#">
            <div class="d-flex align-center justify-center jpname">
              {{ item.jpname }}
            </div>
            <div class="d-flex align-center justify-center name">
              {{ item.name }}
            </div>
          </a>
        </template>
        <template v-slot:item.collectionNo="{ item }">
          {{ item.collectionNo }}
        </template>
        <template v-slot:item.star="{ item }">
          <div class="d-flex pa-2" style="flex-wrap: nowrap !important">
            <div v-for="(star, index) in item.star" :key="index" class="star">
              ★
            </div>
          </div>
        </template>
        <template v-slot:item.zhijie="{ item }">
          <div class="pa-2">
            <img
              :src="
                require(`@/assets/image/icon/class/class_${item.zhijie}_5.png`)
              "
              width="60px"
            />
          </div>
        </template>
        <template v-slot:item.cmdcard="{ item }">
          <div class="d-flex pa-2" style="flex-wrap: nowrap !important">
            <div v-for="(card, index) in item.cmdcard" :key="index">
              <img
                :src="
                  require(`@/assets/image/icon/cmdCard/icon_cmdCard_${card}.png`)
                "
                width="60px"
              />
            </div>
          </div>
        </template>
        <template v-slot:item.baojie="{ item }">
          <div class="d-flex pa-2">
            <div>
              <img
                :src="
                  require(`@/assets/image/icon/cmdCard/icon_cmdCard_${item.baojie}.png`)
                "
                width="60px"
              />
            </div>
          </div>
        </template>
        <template v-slot:item.ImgNo="{ item }">
          <div class="pa-2">
            <router-link
              :to="{
                path: '/ServantDetail',
                query: { No: item.collectionNo },
              }"
            >
              <img
                :src="require(`@/assets/image/icon/faces/${item.ImgNo}0.png`)"
                width="80px"
              />
            </router-link>
          </div>
        </template>
      </v-data-table>
    </div>
  </div>
</template>
<script>
import Servant from "@/config/servant";

export default {
  data: () => {
    return {
      tab: null,
      tableheader: [
        {
          text: "圖示",
          value: "ImgNo",
        },
        { text: "編號", value: "collectionNo" },
        { text: "星數", value: "star" },
        { text: "名稱", value: "name" },
        { text: "職階", value: "zhijie" },
        // { text: "基本HP", value: "minhp" },
        // { text: "最大HP", value: "maxhp" },
        // { text: "基本ATK", value: "minatk" },
        // { text: "最大ATK", value: "maxatk" },
        // { text: "指令卡", value: "cmdcard" },
        { text: "寶具", value: "baojie" },
        { text: "Cost", value: "cost" },
      ],
      zhijies: [
        {
          value: "saber",
          id: 1,
        },
        {
          value: "archer",
          id: 2,
        },
        {
          value: "lancer",
          id: 3,
        },
        {
          value: "rider",
          id: 4,
        },
        {
          value: "caster",
          id: 5,
        },
        {
          value: "assasian",
          id: 6,
        },
        {
          value: "berserker",
          id: 7,
        },
        {
          value: "shielder",
          id: 8,
        },
        {
          value: "avenger",
          id: 10,
        },
        {
          value: "ruler",
          id: 9,
        },
        {
          value: "alterego",
          id: 11,
        },
        {
          value: "mooncancer",
          id: 23,
        },
        {
          value: "foreigner",
          id: 25,
        },
        {
          value: "pretender",
          id: 28,
        },
      ],
      Selectzhijielist: [],
      starlist: [],
    };
  },
  computed: {
    Servantlist() {
      return Servant;
    },
    showdata() {
      if (this.Selectzhijielist.length > 0) {
        let data = this.Servantlist.filter((x) => {
          if (this.Selectzhijielist.indexOf(x.zhijie) !== -1) {
            return x;
          }
        });
        if (this.starlist.length > 0) {
          data = data.filter((x) => {
            if (this.starlist.indexOf(x.star) !== -1) {
              return x;
            }
          });
        }
        return data;
      } else {
        if (this.starlist.length > 0) {
          const data = this.Servantlist.filter((x) => {
            if (this.starlist.indexOf(x.star) !== -1) {
              return x;
            }
          });
          return data;
        }
      }
      return this.Servantlist;
    },
  },
  methods: {
    Selectzhijie(zhijie) {
      if (this.Selectzhijielist.indexOf(zhijie.id) !== -1) {
        this.Selectzhijielist.splice(
          this.Selectzhijielist.indexOf(zhijie.id),
          1
        );
      } else {
        this.Selectzhijielist.push(zhijie.id);
      }
    },
    setstarlist(val) {
      if (this.starlist.indexOf(val) !== -1) {
        this.starlist.splice(this.starlist.indexOf(val), 1);
      } else {
        this.starlist.push(val);
      }
    },
    allzhijie(val) {
      this.Selectzhijielist = [];
      if (val === 1) {
        this.Selectzhijielist = this.zhijies.map((x) => x.id);
      }
    },
    allstar(val) {
      this.starlist = [];
      if (val === 1) {
        this.starlist = [1, 2, 3, 4, 5];
      }
    },
  },
};
</script>



<style lang="scss" scoped>
$zhijie-array: (
  saber: 1,
  archer: 2,
  lancer: 3,
  rider: 4,
  caster: 5,
  assasian: 6,
  berserker: 7,
  shielder: 8,
  avenger: 10,
  ruler: 9,
  alterego: 11,
  mooncancer: 23,
  foreigner: 25,
  pretender: 28,
);

@each $key, $value in $zhijie-array {
  .img_#{$key} {
    background-image: url("~@/assets/image/icon/class/class_#{$value}_1.png");
    background-size: cover;
  }
  .img_#{$key}_on {
    background-image: url("~@/assets/image/icon/class/class_#{$value}_4.png");
    background-size: cover;
  }
}
</style>

<style scoped>
.justify-center {
  justify-content: center;
}
.d-flex {
  display: flex;
  flex-wrap: wrap !important;
}

.bdgray {
  border: 1px solid gray;
}

.pa-1 {
  padding: 4px !important;
}

.pa-2 {
  padding: 8px;
}

.bkmk {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 140px;
  height: 40px;
  background-image: url("~@/assets/image/bkmk_off.png");
  color: white;
}
.active {
  background-image: url("~@/assets/image/bkmk_on.png");
}
.icon {
  width: 40px;
  height: 40px;
}
.img_allon {
  background-image: url("~@/assets/image/icon/class/class_1001_4.png");
  background-size: cover;
}
.img_alloff {
  background-image: url("~@/assets/image/icon/class/class_1001_1.png");
  background-size: cover;
}
.img_starnew {
  background-image: url("~@/assets/image/icon/class/star_new.png");
  background-size: cover;
}
.img_starclear {
  background-image: url("~@/assets/image/icon/class/star_clear.png");
  background-size: cover;
}

.btnstarcancel {
  filter: brightness(0.5);
}

.star {
  color: rgb(255, 213, 0) !important;
  text-shadow: black 1px 1px 1px;
}
.align-center {
  align-items: center;
}
.justify-center {
  justify-content: center;
}
.name {
  color: blue;
}
.jpname {
  color: red;
}
</style>

