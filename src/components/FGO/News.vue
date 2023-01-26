<template>
  <div class="row">
    <card type="">
      <v-alert color="blue-grey" dark>
        <div class="d-flex align-center">
          <div class="pa-1">{{ news.PostDate }}</div>
          <div class="newspan pa-1"></div>
          <div class="pa-1">{{ news.Title }}</div>
        </div>
      </v-alert>

      <div class="d-flex">
        <div
          class="col-sm-6"
          v-for="(item, index) in news.bannerarr"
          :key="index"
        >
          <img :src="require(`@/assets/image${item}`)" alt="" />
        </div>
      </div>
      <div
        class="bluetitle pa-2"
        v-for="(subtitle, index) in news.subtitlearr"
        :key="index"
      >
        {{ subtitle.Subtitle }}
        <span class="notice">({{ subtitle.notice }})</span>
      </div>
      <div class="pa-2" v-for="(item, index) in news.AddItems" :key="index">
        <div v-if="item.title">
          <font color="#094a98">◆</font>
          {{ item.title }}
          <font color="#094a98">◆</font>
        </div>
        <div class="pa-2">
          <div v-if="item.subtitle">{{ item.subtitle }}</div>
          <div class="d-flex">
            <img
              v-for="(img, index2) in item.itemsarr"
              :key="index2"
              :src="require(`@/assets/image${img}`)"
              height="80px"
              alt=""
              class="pa-1 imgborderradius"
            />
          </div>
        </div>
      </div>
    </card>
  </div>
</template>

<script>
export default {
  props: {
    news: Object,
  },
};
</script>

<style scoped>
.pa-1 {
  padding: 4px !important;
}
.pa-2 {
  padding: 8px !important;
}
.pa-4 {
  padding: 16px !important;
}
.align-center {
  align-items: center;
}
.newspan {
  width: 59px;
  height: 19px;
  background-size: cover;
  background-image: url("~@/assets/image/new_tab.png");
}
.d-flex {
  display: flex !important;
  flex-wrap: wrap !important;
}
.whitetitle {
  color: white;
}
.bluetitle {
  color: #2d7dd2;
}
.imgborderradius {
  border-radius: 10px;
}
.notice {
  color: red;
}
</style>
