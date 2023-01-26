<template>
  <v-app>
    <notifications></notifications>
    <router-view :key="$route.fullPath"></router-view>
    <v-btn
      v-scroll="onScroll"
      v-show="fab"
      dark
      fixed
      width="40px"
      style="min-width: 40px"
      bottom
      right
      color="primary"
      @click="toTop"
    >
      <v-img :src="require(`@/assets/image/btn_gotop_on.jpg`)"></v-img>
    </v-btn>
  </v-app>
</template>

<script>
export default {
  data:()=> {
    return{
      fab: false,
    }
  },
  methods: {
    onScroll(e) {
      if (typeof window === "undefined") return;
      const top = window.pageYOffset || e.target.scrollTop || 0;
      this.fab = top > 20;
    },
    toTop () {
      this.$vuetify.goTo(0)
    },
    disableRTL() {
      if (!this.$rtl.isRTL) {
        this.$rtl.disableRTL();
      }
    },
    toggleNavOpen() {
      let root = document.getElementsByTagName("html")[0];
      root.classList.toggle("nav-open");
    },
  },
  mounted() {
    this.$watch("$route", this.disableRTL, { immediate: true });
    this.$watch("$sidebar.showSidebar", this.toggleNavOpen);
  },
};
</script>

<style lang="scss"></style>
