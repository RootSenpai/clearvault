<template>
  <header>
    <nav class="fixed top-0 left-0 right-0 z-50">
      <div class="max-w-7xl mx-auto px-6 md:px-12">
        <div
          class="relative flex items-center justify-between py-2 md:py-4 transition-all duration-300"
          :class="scrolled ? 'bg-[#111]/90 backdrop-blur-xl rounded-3xl border border-white/8 mt-2 px-4' : 'bg-transparent'"
        >
          <NuxtLink to="/" class="flex items-center">
            <span class="font-[Syne] text-lg font-bold text-white tracking-wide">XMARKET</span>
          </NuxtLink>

          <button
            @click="mobileOpen = !mobileOpen"
            aria-label="Toggle navigation"
            class="relative flex h-11 w-12 items-center justify-center rounded lg:hidden"
          >
            <span class="relative block">
              <span class="block h-0.5 w-5 rounded bg-gray-300 transition-transform duration-300" :class="mobileOpen ? 'translate-y-1.5 rotate-45' : ''" />
              <span class="mt-2 block h-0.5 w-5 rounded bg-gray-300 transition-transform duration-300" :class="mobileOpen ? '-translate-y-1 -rotate-45' : ''" />
            </span>
          </button>

          <div
            class="items-center gap-0 lg:flex"
            :class="mobileOpen
              ? 'fixed inset-x-0 top-[60px] z-20 mx-4 mt-2 flex flex-col gap-4 rounded-2xl border border-white/8 bg-[#111]/95 backdrop-blur-xl p-6 shadow-2xl lg:relative lg:inset-auto lg:mx-0 lg:mt-0 lg:flex-row lg:gap-0 lg:border-none lg:bg-transparent lg:p-0 lg:shadow-none'
              : 'hidden lg:flex'"
          >
            <div class="flex flex-col gap-2 lg:flex-row lg:gap-0 lg:pr-4">
              <a
                v-for="link in navLinks"
                :key="link.href"
                :href="link.href"
                class="block py-2 px-3 rounded-lg font-sans text-sm text-text-muted transition-colors hover:text-accent hover:bg-white/5 lg:py-0 lg:px-4 lg:rounded-none lg:hover:bg-transparent"
                @click="mobileOpen = false"
              >
                {{ link.label }}
              </a>
            </div>
            <a
              href="https://discord.gg/bnhwFSU75P"
              target="_blank"
              rel="noopener noreferrer"
              class="flex h-9 items-center justify-center px-6 rounded-full bg-accent font-sans text-sm font-semibold text-background transition-colors duration-200 hover:bg-accent/90"
            >
              Join Discord
            </a>
          </div>
        </div>
      </div>
    </nav>
  </header>
</template>

<script setup lang="ts">
const scrolled = ref(false)
const mobileOpen = ref(false)
const baseURL = useRuntimeConfig().app.baseURL.replace(/\/$/, '')

const pageHref = (path: string) => `${baseURL}${path}`

const navLinks = [
  { href: pageHref('/#services'),  label: 'Services'  },
  { href: pageHref('/#catalog'),   label: 'Catalog'   },
  { href: pageHref('/guides'),     label: 'Guides'    },
  { href: pageHref('/securing'),   label: 'Securing'  },
  { href: pageHref('/terms'),      label: 'Terms'     },
]

onMounted(() => {
  window.addEventListener('scroll', () => {
    scrolled.value = window.scrollY > 20
  }, { passive: true })
})
</script>
