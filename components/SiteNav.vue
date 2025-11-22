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
      <ul class="navbar-menu-center">
        <li
          v-for="item in $siteConfig.mainMenu"
          :key="item.link"
          :class="['navbar-item', { 'is-active': isActive(item) }]"
          @click="handleMenuClick(item)"
        >
          <component
            :is="linkType(item.link)"
            :href="item.link"
            :to="item.link"
            :target="item.target ? item.target : '_self'"
            :class="{ 'has-underline': isActive(item) }"
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
      active: false,
      activeSection: ''
    }
  },
  mounted() {
    this.initScrollSpy()
  },
  beforeDestroy() {
    if (this.sectionObserver) {
      this.sectionObserver.disconnect()
    }
  },
  methods: {
    initScrollSpy() {
      if (!process.client) return

      const sectionIds = this.$siteConfig.mainMenu
        .map((item) => this.sectionIdFromLink(item.link))
        .filter(Boolean)

      if (!sectionIds.length) return

      this.sectionObserver = new window.IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) {
              this.activeSection = entry.target.id
            }
          })
        },
        {
          rootMargin: '-40% 0px -40% 0px'
        }
      )

      sectionIds.forEach((id) => {
        const el = document.getElementById(id)
        if (el) {
          this.sectionObserver.observe(el)
        }
      })
    },
    linkType(link) {
      if (link.startsWith('#') || link.startsWith('http')) {
        return 'a'
      }

      return 'nuxt-link'
    },
    sectionIdFromLink(link) {
      return link.startsWith('#') ? link.slice(1) : null
    },
    isActive(item) {
      const sectionId = this.sectionIdFromLink(item.link)
      return sectionId && sectionId === this.activeSection
    },
    handleMenuClick(item) {
      this.active = false
      const sectionId = this.sectionIdFromLink(item.link)
      if (sectionId) {
        this.activeSection = sectionId
      }
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
.navbar-item .has-underline {
  padding-bottom: 0.25rem;
  border-bottom: 2px solid transparent;
  transition: border-color 0.2s ease;
}
.navbar-item.is-active .has-underline {
  border-color: #1b3c6f;
}
.navbar-menu {
  flex: 1;
  justify-content: center;
}
.navbar-menu-center {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
}
@media screen and (min-width: 1024px) {
  .navbar-menu-center {
    flex-direction: row;
    justify-content: center;
  }
}
.landing-nav {
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(6px);
  border-bottom: 1px solid #e6e6e6;
}
</style>
