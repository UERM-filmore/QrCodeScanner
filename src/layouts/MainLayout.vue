<template>
  <!-- <q-layout view="lHh lpR lFf">
    <q-header elevated class="bg-primary text-white">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />
        <q-toolbar-title> GRADUATE VERIFICATION </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer
      show-if-above
      class="bg-blue-grey-8"
      v-model="leftDrawerOpen"
      side="left"
      bordered
      dark
    >
      <q-list>
        <div class="row justify-center q-mt-lg">
          <q-avatar size="72px">
            <q-img :src="`http://10.107.11.169/getpic/?i=4051`" />
          </q-avatar>
        </div>
        <div class="row justify-center text-weight-bold q-mt-md q-mb-xl">
          COCO MARTIN
        </div>

        <q-item
          clickable
          to="/dashboard"
          id="links"
          active-class="my-menu-link"
        >
          <q-item-section avatar>
            <q-icon name="home" />
          </q-item-section>
          <q-item-section>
            <q-item-label>DASHBOARD</q-item-label>
          </q-item-section>
        </q-item>

        <q-item clickable to="/grades" id="links" active-class="my-menu-link">
          <q-item-section avatar>
            <q-icon name="person" />
          </q-item-section>
          <q-item-section>
            <q-item-label>VERIFICATION RATING</q-item-label>
          </q-item-section>
        </q-item>

        <q-item clickable to="/ledger" id="links" active-class="my-menu-link">
          <q-item-section avatar>
            <q-icon name="folder" />
          </q-item-section>
          <q-item-section>
            <q-item-label>VERIFICATION OF LICENSE</q-item-label>
          </q-item-section>
        </q-item>
        <q-item
          clickable
          @click="persistent = true"
          id="links"
          active-class="my-menu-link"
        >
          <q-item-section avatar>
            <q-icon name="logout" />
          </q-item-section>
          <q-item-section>
            <q-item-label>LOG OUT</q-item-label>
          </q-item-section>
          <q-dialog
            v-model="persistent"
            persistent
            transition-show="scale"
            transition-hide="scale"
          >
            <q-card class="bg-white text-black" style="width: 300px">
              <q-card-section>
                <div class="text-h6">LOGOUT</div>
              </q-card-section>

              <q-card-section class="q-pt-none">
                Are you sure you want to logout?
              </q-card-section>
              <q-card-actions align="right" class="bg-white">
                <q-btn
                  flat
                  class="text-green"
                  label="NO"
                  v-close-popup
                  @click="persistent = false"
                /><q-btn
                  flat
                  class="text-green"
                  label="YES"
                  v-close-popup
                  to="/"
                  @click="logout(), (persistent = true)"
                />
              </q-card-actions>
            </q-card>
          </q-dialog>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout> -->

  <q-layout view="hHh lpR fFf">
    <q-header elevated class="bg-primary text-white" height-hint="98">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="../assets//uerm-logo.png" />
          </q-avatar>
          UERM GRADUATE VERIFICATION
        </q-toolbar-title>
      </q-toolbar>

      <q-tabs align="left">
        <!-- <q-route-tab to="/page1" label="VERIFICATION OF RATING" /> -->
        <q-route-tab to="/" label="VERIFICATION BY NAME" />
        <!-- <q-route-tab
          to="/page3"
          label="VERIFICATION OF LICENSE(BY LICENSE NO.)"
        /> -->
        <q-route-tab to="/verify-scan" label="VERIFICATION BY SCANNING" />
      </q-tabs>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from "vue";

import { mapGetters } from "vuex";

export default defineComponent({
  name: "MainLayout",
  components: {},
  data() {
    return {
      leftDrawerOpen: false,
    };
  },
  methods: {
    toggleLeftDrawer() {
      this.leftDrawerOpen = !this.leftDrawerOpen;
    },
  },
  computed: {
    projectName() {
      return process.env.PROJECT_NAME;
    },
    projectShortName() {
      return process.env.PROJECT_SHORT_NAME;
    },
    projectVersion() {
      return process.env.PROJECT_VERSION;
    },
    currentYear() {
      return new Date().getFullYear();
    },
    ...mapGetters({
      navLinks: "helpers/navLinks",
    }),
  },
});
</script>
