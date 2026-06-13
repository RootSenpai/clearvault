<template>
  <footer class="border-t border-border">
    <div class="max-w-7xl mx-auto px-6 md:px-12 pt-12 pb-0">

      <div class="relative rounded-2xl border border-white/6 bg-surface overflow-hidden mb-14">
        <div aria-hidden="true" class="absolute inset-0 pointer-events-none">
          <div class="absolute -top-20 left-1/3 w-[320px] h-[120px] rounded-full bg-accent/[0.05] blur-[70px]" />
        </div>

        <div class="relative z-10 flex flex-col sm:flex-row items-center justify-between gap-6 px-7 py-6">

          <div class="flex items-center gap-4 shrink-0">
            <div class="w-10 h-10 rounded-xl bg-[#5865F2]/15 border border-[#5865F2]/25 flex items-center justify-center shrink-0">
              <svg class="w-5 h-5 text-[#5865F2]" viewBox="0 0 24 24" fill="currentColor">
                <path d="M19.27 5.33C17.94 4.71 16.5 4.26 15 4a.09.09 0 00-.07.03c-.18.33-.39.76-.53 1.09a16.09 16.09 0 00-4.8 0c-.14-.34-.35-.76-.54-1.09-.01-.02-.04-.03-.07-.03-1.5.26-2.93.71-4.27 1.33-.01 0-.02.01-.03.02-2.72 4.07-3.47 8.03-3.1 11.95 0 .02.01.04.03.05 1.8 1.32 3.53 2.12 5.24 2.65.03.01.06 0 .07-.02.4-.55.76-1.13 1.07-1.74.02-.04 0-.08-.04-.09-.57-.22-1.11-.48-1.64-.78-.04-.02-.04-.08-.01-.11.11-.08.22-.17.33-.25.02-.02.05-.02.07-.01 3.44 1.57 7.15 1.57 10.55 0 .02-.01.05 0 .07.01.11.09.22.17.33.26.04.03.04.09-.01.11-.52.31-1.07.56-1.64.78-.04.01-.05.06-.04.09.32.61.68 1.19 1.07 1.74.03.01.06.02.09.01 1.72-.53 3.45-1.33 5.25-2.65.02-.01.03-.03.03-.05.44-4.53-.73-8.46-3.1-11.95-.01-.01-.02-.02-.04-.02zM8.52 14.91c-1.03 0-1.89-.95-1.89-2.12s.84-2.12 1.89-2.12c1.06 0 1.9.96 1.89 2.12 0 1.17-.84 2.12-1.89 2.12zm6.97 0c-1.03 0-1.89-.95-1.89-2.12s.84-2.12 1.89-2.12c1.06 0 1.9.96 1.89 2.12 0 1.17-.83 2.12-1.89 2.12z"/>
              </svg>
            </div>
            <div>
              <p class="font-sans text-[10px] font-bold uppercase tracking-widest text-text-muted/50 leading-none mb-1">Discord Community</p>
              <p class="font-[Syne] text-base font-bold text-white leading-none">Xmarket</p>
            </div>
          </div>

          <div class="flex items-center gap-4">
            <div v-if="avatarStack.length" class="flex items-center">
              <img
                v-for="(m, i) in avatarStack"
                :key="m.id"
                :src="m.avatar_url"
                :alt="m.username"
                :style="{ zIndex: avatarStack.length - i, marginLeft: i === 0 ? '0' : '-8px' }"
                class="w-8 h-8 rounded-full border-2 border-surface object-cover shrink-0"
                loading="lazy"
              />
            </div>
            <div class="flex items-center gap-2">
              <span class="w-2 h-2 rounded-full bg-emerald-400 animate-pulse shrink-0" />
              <span class="font-[Syne] text-xl font-bold text-white tabular-nums">{{ widget?.presence_count ?? '—' }}</span>
              <span class="font-sans text-sm text-text-muted">online</span>
            </div>
          </div>

          <a
            href="https://discord.gg/bnhwFSU75P"
            target="_blank"
            rel="noopener noreferrer"
            class="inline-flex items-center gap-2 h-10 px-5 rounded-full bg-accent font-sans text-sm font-semibold text-background transition-colors duration-200 hover:bg-accent/90 shrink-0"
          >
            Join Server
            <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="2.5">
              <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3" />
            </svg>
          </a>
        </div>
      </div>

      <div class="grid grid-cols-1 gap-10 sm:grid-cols-2 lg:grid-cols-5 pb-16">

        <div class="lg:col-span-1">
          <NuxtLink to="/" class="flex items-center mb-5">
            <span class="font-[Syne] text-xl font-bold text-white tracking-wide">Xmarket</span>
          </NuxtLink>
          <p class="font-sans text-sm text-text-muted leading-relaxed">
            Discord-based digital marketplace. Purchases delivered digitally after payment review.
          </p>
        </div>

        <div>
          <h4 class="font-sans text-sm font-semibold text-white mb-5">Services</h4>
          <ul class="space-y-3">
            <li><a :href="pageHref('/#services')" class="font-sans text-sm text-text-muted hover:text-white transition-colors">What we offer</a></li>
            <li><a :href="pageHref('/#catalog')"  class="font-sans text-sm text-text-muted hover:text-white transition-colors">Catalog</a></li>
            <li><a :href="pageHref('/#commands')" class="font-sans text-sm text-text-muted hover:text-white transition-colors">Commands</a></li>
          </ul>
        </div>

        <div>
          <h4 class="font-sans text-sm font-semibold text-white mb-5">Support</h4>
          <ul class="space-y-3">
            <li>
              <a href="https://discord.gg/bnhwFSU75P" target="_blank" rel="noopener noreferrer" class="font-sans text-sm text-text-muted hover:text-white transition-colors">
                Discord server
              </a>
            </li>
            <li>
              <a href="https://discord.gg/bnhwFSU75P" target="_blank" rel="noopener noreferrer" class="font-sans text-sm text-text-muted hover:text-white transition-colors">
                Open a ticket
              </a>
            </li>
          </ul>
        </div>

        <div>
          <h4 class="font-sans text-sm font-semibold text-white mb-5">Guides</h4>
          <ul class="space-y-3">
            <li><NuxtLink to="/guides" class="font-sans text-sm text-text-muted hover:text-white transition-colors">Command Guides</NuxtLink></li>
            <li><NuxtLink to="/securing" class="font-sans text-sm text-text-muted hover:text-white transition-colors">Securing</NuxtLink></li>
            <li><a href="https://discord.gg/bnhwFSU75P" target="_blank" rel="noopener noreferrer" class="font-sans text-sm text-text-muted hover:text-white transition-colors">Discord Support</a></li>
          </ul>
        </div>
