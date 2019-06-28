<template lang="pug">
  q-layout(view='hHh lpR fFf')
    q-header(elevated)
      q-toolbar
        q-btn(flat, dense, round, @click='leftDrawerOpen = !leftDrawerOpen', aria-label='Menu')
          q-icon(name='menu')
        q-toolbar-title.absolute-center
          | ToDo
    // フッター
    q-footer
      q-tabs
        q-route-tab(v-for="(nav, index) in navs" :key="index" :to="nav.to" :icon="nav.icon" :label="nav.label")
    q-drawer(v-model='leftDrawerOpen', :breakpoint="767" :width="250" bordered, content-class='bg-primary')
      q-list(dark)
        q-item-label(header) ナビゲーション
        q-item.text-grey-4(v-for="(nav, index) in navs" :key="index" clickable :to="nav.to" exact)
          q-item-section(avatar)
            q-icon(:name="nav.icon")
          q-item-section
            q-item-label {{ nav.label }}
    q-page-container
      router-view
</template>

<script lang="ts">
import { openURL } from 'quasar'

import Vue from 'vue'

export default Vue.extend({
  name: 'MyLayout',
  data () {
    return {
      leftDrawerOpen: this.$q.platform.is.desktop,
      navs: [
        {
          label: 'ToDo',
          icon: 'list',
          to: '/'
        },
        {
          label: '設定',
          icon: 'settings',
          to: '/settings'
        }
      ]
    }
  },
  methods: {
    openURL
  }
})
</script>

<style lang="scss">
  @media screen and (min-width: 768px) {
    .q-footer {
      display: none;
    }
  }

  .q-drawer .q-router-link--exact-active {
    color: white !important;
  }
</style>
