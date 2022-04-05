<template>
  <div id="app">
    <v-app>
      <router-view id="view" />
    </v-app>
  </div>
</template>

<script>
//main vue template but the actual stuff is in /views/Index
export default {
  name: "App",
};
</script>
<style lang="stylus">
#app, #wrapper {
  background: #efefef;
}
</style>
