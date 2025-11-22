<template>
  <nav
    class="navbar has-shadow is-fixed-top landing-nav"
    role="navigation"
    aria-label="main navigation"
  >
    <div class="navbar-brand">
      <nuxt-link class="navbar-item" to="/">
        <site-logo v-if="$siteConfig.logo === 'logo-component'" />
        <img
          v-else
          :src="$siteConfig.logo"
          :alt="$siteConfig.siteName"
          class="logo"
        />
      </nuxt-link>
      <hamburger-button @click="active = !active" />
    </div>

    <div
      :class="{
        'navbar-menu': true,
        'is-active': active
      }"
    >
      <ul class="navbar-end">
        <li
          v-for="item in $siteConfig.mainMenu"
          :key="item.link"
          class="navbar-item"
          @click="active = false"
        >
          <component
            :is="linkType(item.link)"
            :href="item.link"
            :to="item.link"
            :target="item.target ? item.target : '_self'"
          >
            {{ item.name }}
          </component>
        </li>
      </ul>
    </div>
  </nav>
</template>
<script>
import HamburgerButton from '~/components/HamburgerButton'
export default {
  name: 'SiteNav',
  components: { HamburgerButton },
  data() {
    return {
      active: false
    }
  },
  methods: {
    linkType(link) {
      if (link.startsWith('#') || link.startsWith('http')) {
        return 'a'
      }

      return 'nuxt-link'
    }
  }
}
</script>
<style lang="scss" scoped>
.navbar-item img {
  max-height: 2rem;
}
.navbar-burger {
  height: auto;
}

.navbar-menu a {
  display: block;
}
.landing-nav {
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(6px);
  border-bottom: 1px solid #e6e6e6;
}
</style>
