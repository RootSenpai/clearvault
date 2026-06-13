<template>
  <div>
    <section class="relative pt-20 pb-0 overflow-hidden">
      <div aria-hidden="true" class="absolute inset-0 -z-10 grid grid-cols-2 -space-x-52 opacity-[0.08]">
        <div class="h-48 bg-gradient-to-br from-accent to-[#ff6b6b] blur-[100px]" />
        <div class="h-28 bg-gradient-to-r from-accent-secondary to-accent blur-[100px]" />
      </div>

      <div class="relative z-10 max-w-7xl mx-auto px-6 md:px-12">

        <div class="text-center max-w-lg mx-auto mb-12">
          <h1 class="font-[Syne] text-4xl md:text-5xl font-extrabold text-white mb-4 leading-[1.1]">Securing your product</h1>
          <p class="font-sans text-[15px] text-text-muted leading-relaxed">Learn how to protect your purchased digital products, monitor for unauthorized changes, and avoid common issues.</p>
        </div>

        <div class="grid grid-cols-3 gap-3 max-w-sm mx-auto pb-12">
          <button
            v-for="tab in tabs"
            :key="tab.id"
            :disabled="tab.tba"
            @click="!tab.tba && (activeTab = tab.id)"
            class="group relative flex flex-col items-center gap-3 py-6 px-3 rounded-2xl border transition-all duration-200 focus-visible:outline-none"
            :class="tab.tba
              ? 'border-white/4 bg-surface/50 cursor-not-allowed'
              : activeTab === tab.id
                ? 'border-accent/40 bg-accent/[0.07]'
                : 'border-white/6 bg-surface hover:border-white/12 hover:bg-white/[0.04]'"
          >
            <span v-if="activeTab === tab.id && !tab.tba" class="absolute top-2.5 right-2.5 w-1.5 h-1.5 rounded-full bg-accent" />
            <img
              :src="tab.icon"
              :alt="tab.label"
              class="w-9 h-9 object-contain transition-opacity"
              :class="tab.tba ? 'opacity-20 grayscale' : 'opacity-100'"
            />
            <div class="flex flex-col items-center gap-1">
              <span
                class="font-sans text-xs font-semibold transition-colors leading-none"
                :class="tab.tba ? 'text-text-muted/30' : activeTab === tab.id ? 'text-white' : 'text-text-muted group-hover:text-white'"
              >{{ tab.label }}</span>
              <span v-if="tab.tba" class="font-sans text-[8px] font-bold uppercase tracking-widest text-text-muted/30">TBA</span>
            </div>
          </button>
        </div>

      </div>
    </section>

    <div class="max-w-7xl mx-auto px-6 md:px-12 py-10 pb-24">
      <FortniteSecuring v-if="activeTab === 'fortnite'" />
    </div>
  </div>
</template>

<script setup lang="ts">
useSeoMeta({
  title: 'Securing Your Product — Xmarket',
  ogTitle: 'Xmarket — Securing Your Product',
  description: 'Learn how to protect your purchased digital products, monitor for unauthorized changes, and avoid common issues.',
  ogDescription: 'Learn how to protect your purchased digital products, monitor for unauthorized changes, and avoid common issues.',
})

const activeTab = ref('fortnite')

const tabs = [
  { id: 'fortnite',  label: 'Fortnite',  tba: false, icon: 'https://img.icons8.com/color/48/fortnite.png' },
  { id: 'valorant',  label: 'Valorant',  tba: true,  icon: 'https://img.icons8.com/color/48/valorant.png' },
  { id: 'minecraft', label: 'Minecraft', tba: true,  icon: 'https://img.icons8.com/color/48/minecraft-logo.png' },
]
</script>
