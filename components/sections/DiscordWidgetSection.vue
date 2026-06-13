<template>
  <section class="py-16">
    <div class="max-w-7xl mx-auto px-6 md:px-12">
      <div class="reveal anim-fade-in-bottom relative rounded-2xl border border-white/6 bg-surface overflow-hidden">

        <div aria-hidden="true" class="absolute -top-24 left-1/2 -translate-x-1/2 w-[500px] h-[200px] rounded-full bg-accent/[0.06] blur-[80px] pointer-events-none" />

        <div class="relative z-10 p-8 md:p-10">

          <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-5 mb-8">
            <div class="flex items-center gap-4">
              <div class="w-11 h-11 rounded-xl bg-[#5865F2]/15 border border-[#5865F2]/25 flex items-center justify-center shrink-0">
                <svg class="w-5 h-5 text-[#5865F2]" viewBox="0 0 24 24" fill="currentColor">
                  <path d="M19.27 5.33C17.94 4.71 16.5 4.26 15 4a.09.09 0 00-.07.03c-.18.33-.39.76-.53 1.09a16.09 16.09 0 00-4.8 0c-.14-.34-.35-.76-.54-1.09-.01-.02-.04-.03-.07-.03-1.5.26-2.93.71-4.27 1.33-.01 0-.02.01-.03.02-2.72 4.07-3.47 8.03-3.1 11.95 0 .02.01.04.03.05 1.8 1.32 3.53 2.12 5.24 2.65.03.01.06 0 .07-.02.4-.55.76-1.13 1.07-1.74.02-.04 0-.08-.04-.09-.57-.22-1.11-.48-1.64-.78-.04-.02-.04-.08-.01-.11.11-.08.22-.17.33-.25.02-.02.05-.02.07-.01 3.44 1.57 7.15 1.57 10.55 0 .02-.01.05 0 .07.01.11.09.22.17.33.26.04.03.04.09-.01.11-.52.31-1.07.56-1.64.78-.04.01-.05.06-.04.09.32.61.68 1.19 1.07 1.74.03.01.06.02.09.01 1.72-.53 3.45-1.33 5.25-2.65.02-.01.03-.03.03-.05.44-4.53-.73-8.46-3.1-11.95-.01-.01-.02-.02-.04-.02zM8.52 14.91c-1.03 0-1.89-.95-1.89-2.12s.84-2.12 1.89-2.12c1.06 0 1.9.96 1.89 2.12 0 1.17-.84 2.12-1.89 2.12zm6.97 0c-1.03 0-1.89-.95-1.89-2.12s.84-2.12 1.89-2.12c1.06 0 1.9.96 1.89 2.12 0 1.17-.83 2.12-1.89 2.12z"/>
                </svg>
              </div>
              <div>
                <p class="font-sans text-[10px] font-bold uppercase tracking-widest text-text-muted/60 mb-0.5">Discord Server</p>
                <h3 class="font-[Syne] text-lg font-bold text-white leading-none">Xmarket</h3>
              </div>
            </div>

            <div class="flex items-center gap-5">
              <div class="flex items-center gap-2 px-4 py-2 rounded-full border border-emerald-500/20 bg-emerald-500/[0.07]">
                <span class="w-2 h-2 rounded-full bg-emerald-400 animate-pulse shrink-0" />
                <span class="font-sans text-sm font-semibold text-emerald-400">{{ widget?.presence_count ?? '—' }} online</span>
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

          <div class="border-t border-white/[0.05] mb-7" />

          <div v-if="visibleMembers.length">
            <p class="font-sans text-[10px] font-bold uppercase tracking-widest text-text-muted/50 mb-4">Active members</p>
            <div class="flex flex-wrap gap-2.5">
              <div
                v-for="member in visibleMembers"
                :key="member.id"
                class="group relative flex items-center gap-2.5 pl-1.5 pr-3.5 py-1.5 rounded-full border border-white/[0.06] bg-secondary transition-colors hover:border-white/[0.12]"
              >
                <div class="relative shrink-0">
                  <img
                    :src="member.avatar_url"
                    :alt="member.username"
                    class="w-6 h-6 rounded-full object-cover"
                    loading="lazy"
                  />
                  <span
                    class="absolute -bottom-0.5 -right-0.5 w-2.5 h-2.5 rounded-full border-2 border-secondary"
                    :class="{
                      'bg-emerald-400': member.status === 'online',
                      'bg-yellow-400':  member.status === 'idle',
                      'bg-red-500':     member.status === 'dnd',
                      'bg-zinc-500':    member.status === 'offline',
                    }"
                  />
                </div>
                <span class="font-sans text-xs text-text-muted group-hover:text-white transition-colors leading-none">{{ member.username }}</span>
              </div>

              <div v-if="overflowCount > 0" class="flex items-center px-3.5 py-1.5 rounded-full border border-white/[0.06] bg-secondary">
                <span class="font-sans text-xs text-text-muted">+{{ overflowCount }} more</span>
              </div>
            </div>
          </div>

          <div v-else class="flex flex-wrap gap-2.5">
            <div v-for="n in 16" :key="n" class="h-9 w-28 rounded-full bg-white/[0.04] animate-pulse" />
          </div>

        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
const MAX_VISIBLE = 24

interface WidgetMember {
  id: string
  username: string
  status: 'online' | 'idle' | 'dnd' | 'offline'
  avatar_url: string
}

interface WidgetData {
  id: string
  name: string
  instant_invite: string
  presence_count: number
  members: WidgetMember[]
}

const { data: widget } = await useFetch<WidgetData>(
  'https://discord.com/api/guilds/1324585061223497842/widget.json',
  {
    key: 'discord-widget',
    server: false,
  }
)

const statusOrder: Record<string, number> = { online: 0, idle: 1, dnd: 2, offline: 3 }

const sortedMembers = computed(() =>
  [...(widget.value?.members ?? [])].sort(
    (a, b) => (statusOrder[a.status] ?? 3) - (statusOrder[b.status] ?? 3)
  )
)

const visibleMembers = computed(() => sortedMembers.value.slice(0, MAX_VISIBLE))
const overflowCount  = computed(() => Math.max(0, (widget.value?.presence_count ?? 0) - MAX_VISIBLE))
</script>
