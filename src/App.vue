<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app clipped mini-variant expand-on-hover color="light-blue darken-4">
      <v-list dense>
        <v-list-item v-for="item in items" :key="item.text" link>
          <v-list-item-action>
            <v-icon color="white">{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title class="white--text">
              {{ item.text }}
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <!-- <v-subheader class="mt-4 grey--text text--darken-1">SUBSCRIPTIONS</v-subheader> -->
        <!-- <v-list>
          <v-list-item
            v-for="item in items2"
            :key="item.text"
            link
          >
            <v-list-item-avatar>
              <img
                :src="`https://randomuser.me/api/portraits/men/${item.picture}.jpg`"
                alt=""
              >
            </v-list-item-avatar>
            <v-list-item-title v-text="item.text" />
          </v-list-item>
        </v-list> -->
        <v-list-item class="mt-4" link>
          <v-list-item-action>
            <v-icon color="grey darken-1">mdi-clock-outline</v-icon>
          </v-list-item-action>
          <v-list-item-title class="grey--text text--darken-1"
            >Tabs Hours Report</v-list-item-title
          >
        </v-list-item>
        <v-list-item>
          <v-switch v-model="$vuetify.theme.dark" primary label="Dark" />
        </v-list-item>
        <!-- <v-list-item link>
          <v-list-item-action>
            <v-icon color="grey darken-1">mdi-settings</v-icon>
          </v-list-item-action>
          <v-list-item-title class="grey--text text--darken-1">Manage Subscriptions</v-list-item-title>
        </v-list-item> -->
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app clipped-left color="light-blue darken-3" dense>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-icon class="mx-4" large>
        mdi-image-filter-hdr
      </v-icon>
      <v-toolbar-title class="mr-12 align-center">
        <span class="headline white--text"
          >LONE<span class="green--text">PEAK</span>
          <span class="body-2">Visualization Group</span></span
        >
      </v-toolbar-title>
      <v-spacer />
      <v-row align="center" style="max-width: 650px">
        <v-text-field
          :append-icon-cb="() => {}"
          placeholder="Search..."
          single-line
          dense
          append-icon="mdi-magnify"
          color="white"
          hide-details
        />
        
      </v-row>
    </v-app-bar>

    <v-content>
      <v-container class="fill-height mx-0" fluid>
        <router-view></router-view>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>

export default {
  props: {
    source: String
  },
  data: () => ({
    drawer: null,
    items: [
      { icon: "mdi-plus", text: "Add New Case", color: "" },
      { icon: "mdi-check", text: "Task List", color: "" },
      {
        icon: "mdi-account-multiple-check",
        text: "Manager Task List",
        color: ""
      },
      { icon: "mdi-account-check", text: "Expert Task List", color: "" },
      { icon: "mdi-domain", text: "Associate Management", color: "" },
      { icon: "mdi-account-group", text: "Clients & Contacts", color: "" },
      { icon: "mdi-trending-up", text: "Marketing", color: "" },
      { icon: "mdi-text-box-plus", text: "New Cases", color: "" },
      { icon: "mdi-text-box-check", text: "Cases Closing", color: "" },
      { icon: "mdi-text-box-remove", text: "Closed Cases", color: "" },
      { icon: "mdi-bullseye-arrow", text: "Template Accuracy", color: "" },
      { icon: "mdi-cog", text: "Settings", color: "" }
    ]
    // items2: [
    //   { picture: 28, text: 'Joseph' },
    //   { picture: 38, text: 'Apple' },
    //   { picture: 48, text: 'Xbox Ahoy' },
    //   { picture: 58, text: 'Nokia' },
    //   { picture: 78, text: 'MKBHD' },
    // ],
  }),
};
</script>
