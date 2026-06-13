<template>
  <div>
    <section class="relative pt-20 pb-0 overflow-hidden">
      <div aria-hidden="true" class="absolute inset-0 -z-10 grid grid-cols-2 -space-x-52 opacity-[0.08]">
        <div class="h-48 bg-gradient-to-br from-accent to-[#ff6b6b] blur-[100px]" />
        <div class="h-28 bg-gradient-to-r from-accent-secondary to-accent blur-[100px]" />
      </div>

      <div class="relative z-10 max-w-7xl mx-auto px-6 md:px-12">

        <div class="text-center max-w-lg mx-auto mb-12">
          <h1 class="font-[Syne] text-4xl md:text-5xl font-extrabold text-white mb-4 leading-[1.1]">How to use the bot</h1>
          <p class="font-sans text-[15px] text-text-muted leading-relaxed">Step-by-step guides for finding, filtering, and buying digital products through Xmarket's Discord bot.</p>
        </div>

        <div class="grid grid-cols-2 sm:grid-cols-5 gap-3 max-w-2xl mx-auto pb-12">
          <button
            v-for="tab in tabs"
            :key="tab.id"
            @click="activeTab = tab.id"
            class="group relative flex flex-col items-center gap-3 py-6 px-3 rounded-2xl border transition-all duration-200 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-accent"
            :class="activeTab === tab.id
              ? 'border-accent/40 bg-accent/[0.07]'
              : 'border-white/6 bg-surface hover:border-white/12 hover:bg-white/[0.04]'"
          >
            <span v-if="activeTab === tab.id" class="absolute top-2.5 right-2.5 w-1.5 h-1.5 rounded-full bg-accent" />
            <img v-if="tab.icon" :src="tab.icon" :alt="tab.label" class="w-9 h-9 object-contain" />
            <svg v-else class="w-9 h-9 text-accent" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="1.5">
              <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 21v-7.5a.75.75 0 01.75-.75h3a.75.75 0 01.75.75V21m-4.5 0H2.36m11.14 0H18m0 0h3.64m-1.39 0V9.349m-16.5 11.65V9.35m0 0a3.001 3.001 0 003.75-.615A2.993 2.993 0 009.75 9.75c.896 0 1.7-.393 2.25-1.016a2.993 2.993 0 002.25 1.016c.896 0 1.7-.393 2.25-1.016a3.001 3.001 0 003.75.614m-16.5 0a3.004 3.004 0 01-.621-4.72L4.318 3.44A1.5 1.5 0 015.378 3h13.243a1.5 1.5 0 011.06.44l1.19 2.189a3 3 0 01-.621 4.72m-13.5 8.65h3.75a.75.75 0 00.75-.75V13.5a.75.75 0 00-.75-.75H6.75a.75.75 0 00-.75.75v3.75c0 .415.336.75.75.75z" />
            </svg>
            <span
              class="font-sans text-xs font-semibold transition-colors leading-none"
              :class="activeTab === tab.id ? 'text-white' : 'text-text-muted group-hover:text-white'"
            >{{ tab.label }}</span>
          </button>
        </div>

      </div>
    </section>

    <div class="max-w-7xl mx-auto px-6 md:px-12 py-10 pb-24">
      <FortniteGuide v-if="activeTab === 'fortnite'" />
      <ValorantGuide v-if="activeTab === 'valorant'" />
      <MinecraftGuide v-if="activeTab === 'minecraft'" />
      <RustGuide v-if="activeTab === 'rust'" />
      <MarketGuide v-if="activeTab === 'market'" />
    </div>
  </div>
</template>

<script setup lang="ts">
useSeoMeta({
  title: 'Guides — Xmarket',
  ogTitle: 'Xmarket Guides — How to Use the Bot',
  description: 'Step-by-step guides for finding, filtering, and buying digital products through Xmarket\'s Discord bot.',
  ogDescription: 'Step-by-step guides for finding, filtering, and buying digital products through Xmarket\'s Discord bot.',
})

const activeTab = ref('fortnite')

const tabs = [
  { id: 'fortnite',  label: 'Fortnite',  icon: 'https://img.icons8.com/color/48/fortnite.png' },
  { id: 'valorant',  label: 'Valorant',  icon: 'https://img.icons8.com/color/48/valorant.png' },
  { id: 'minecraft', label: 'Minecraft', icon: 'https://img.icons8.com/color/48/minecraft-logo.png' },
  { id: 'rust',      label: 'Rust',      icon: 'https://img.icons8.com/?size=256&id=NAL2lztANaO6&format=png' },
  { id: 'market',    label: 'Market',    icon: null },
]
</script>
