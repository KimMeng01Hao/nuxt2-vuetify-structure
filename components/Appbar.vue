<template>
  <div>
    <v-navigation-drawer v-model="drawer" fixed app 
      color="primary">
      <v-row class="pa-5">
        <v-col cols="6">
          <v-row justify="end">
            <v-avatar size="48">
              <v-img
                lazy-src="https://picsum.photos/id/11/10/6"
                height="50"
                contain
                src="https://cdn.iconscout.com/icon/free/png-256/web-1158-437300.png"
              ></v-img
            ></v-avatar>
          </v-row>
        </v-col>
        <v-col cols="6" align-self="center">
          <!-- <v-row class="text-center" align="center" justify="center"> -->
          WebApp
          <!-- </v-row> -->
        </v-col></v-row
      >
      <!-- <v-divider /> -->
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar fixed app>
      <v-btn icon @click.stop="drawer = !drawer">
        <v-icon>{{ drawer == true ? 'mdi-close' : 'mdi-menu' }}</v-icon>
      </v-btn>
      <!-- <v-app-bar-nav-icon /> -->
      <v-toolbar-title v-text="title" />
      <v-spacer />
      
      <v-menu bottom left>
        <template v-slot:activator="{ on, attrs }">
          <v-btn icon color="grey" v-bind="attrs" v-on="on">
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>
        </template>

        <v-list>
          <v-list-item>
            <v-list-item-title>Click Me 1</v-list-item-title>
          </v-list-item>

          <v-list-item>
            <v-list-item-title>Click Me 2</v-list-item-title>
          </v-list-item>

          <v-list-item>
            <v-list-item-title>Click Me 3</v-list-item-title>
          </v-list-item>

          <v-list-item>
            <v-list-item-title>Click Me 4</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
      <v-btn icon @click="rightDrawer = !rightDrawer">
        <v-icon>{{
          rightDrawer == true ? 'mdi-chevron-right' : 'mdi-chevron-left'
        }}</v-icon>
      </v-btn>
    </v-app-bar>

    <v-navigation-drawer v-model="rightDrawer" app right>
      <v-list>
        <v-list-item @click.native="right = !right">
          <v-list-item-action>
            <v-icon light> mdi-repeat </v-icon>
          </v-list-item-action>
          <v-list-item-title>Switch drawer (click me)</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </div>
</template>


<script>
export default {
  name: 'AppBarPage',
  data() {
    return {
      clipped: false,
      drawer: false,
      right: true,
      rightDrawer: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/',
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire',
        },
      ],
    }
  },
  methods: {
    onClickOutsideStandard() {
      this.rightDrawer = false
    },
  },
}
</script>
