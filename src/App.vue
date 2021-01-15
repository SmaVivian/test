<template>
  <v-app class="g-app" id="app">
    <cmpHeader></cmpHeader>
    <v-main :class="{'app-mobile': $vuetify.breakpoint.mobile}">
      <v-container fluid>
        <cmpBread></cmpBread>
        <!-- 如果使用 vue-router -->
        <router-view></router-view>
      </v-container>
      <!-- <router-view></router-view> -->
    </v-main>
  </v-app>
</template>

<script>
import cmpHeader from '@cmp/header'
import cmpBread from '@cmp/bread'
export default {
  name: 'App',
  components: { cmpHeader, cmpBread },
  data: () => ({
    //
  }),
};
</script>

<style lang="scss">
// @import '@assets/css/theme.scss';
</style>
