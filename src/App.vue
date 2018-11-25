<template>
  <div class="page-container">
    <md-app md-mode="reveal">
      <md-app-toolbar class="md-primary">
        <md-button class="md-icon-button" @click="menuVisible = !menuVisible">
          <md-icon>menu</md-icon>
        </md-button>
        <span class="md-title">TODO LIST</span>
      </md-app-toolbar>

      <md-app-drawer :md-active.sync="menuVisible">
        <md-list >

          <!-- <md-list-item>
            <md-avatar>
              <img src="https://placeimg.com/40/40/people/2" alt="People">
            </md-avatar>

            <div class="md-list-item-text">
              <span>binatoouser@binatoo.com</span>
              <span>(650) 555-1234</span>
            </div>

          </md-list-item> -->

          <md-divider class="md-inset"></md-divider>

          <md-list-item >
            <md-icon>move_to_inbox</md-icon>
            <router-link class="md-list-item-text" to="/Todo" >ToDo List</router-link>
          </md-list-item>
        </md-list>
      </md-app-drawer>
      <md-app-content>
        <router-view></router-view>
      </md-app-content>
    </md-app>
  </div>
</template>

<style lang="scss" scoped>
  .md-app {
    max-height: 90%;
    border: 1px solid rgba(#000, .12);
  }
   // Demo purposes only
  .md-drawer {
    width: 230px;
    max-width: calc(100vw - 125px);
  }
</style>

<script>
export default {
  name: 'Reveal',
  data: () => ({
    menuVisible: false
  })
}
</script>
