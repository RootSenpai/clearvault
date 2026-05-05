<template>
  <section id="commands" class="py-24">
    <div class="max-w-7xl mx-auto px-6 md:px-12">
      <div class="grid gap-10 lg:grid-cols-2 lg:gap-16 items-start">

        <div>
          <p class="font-sans text-xs font-semibold uppercase tracking-widest text-accent mb-4 reveal anim-fade-in-bottom">Commands</p>
          <h2 class="font-[Syne] text-4xl md:text-5xl font-bold text-white leading-tight mb-5 reveal anim-slide-in-left">
            Four commands run<br>the whole shop.
          </h2>
          <p class="font-sans text-text-muted leading-relaxed mb-12 max-w-md reveal anim-fade-in-bottom" style="animation-delay: 0.15s">
            No dashboard, no extra accounts. Browse, check out, and manage everything from inside the Discord.
          </p>

          <div class="grid sm:grid-cols-2 gap-px rounded-2xl overflow-hidden border border-white/6 bg-white/[0.04]">
            <div
              v-for="(cmd, i) in commands"
              :key="cmd.cmd"
              class="group relative p-5 bg-surface hover:bg-surface-hover transition-colors duration-200 reveal anim-fade-in-bottom"
              :style="{ animationDelay: i * 0.08 + 's' }"
            >
              <code class="font-mono text-xs text-accent block mb-3">{{ cmd.cmd }}</code>
              <h3 class="font-[Syne] text-base font-bold text-white mb-1.5">{{ cmd.title }}</h3>
              <p class="font-sans text-xs text-text-muted leading-relaxed">{{ cmd.desc }}</p>
            </div>
          </div>

        </div>

        <div class="block min-w-0 reveal anim-fade-in-bottom" style="animation-delay: 0.2s">
          <div class="rounded-2xl border border-white/6 bg-surface p-4 sm:p-6 space-y-5">

            <div class="flex items-start gap-3">
              <img
                src="https://cdn.discordapp.com/avatars/797603163360067614/56740bd7c61b9027220031bc97498f8e.png?size=512"
                alt="Nfx - switch swapped"
                class="w-9 h-9 sm:w-10 sm:h-10 rounded-full object-cover shrink-0"
              />
              <div class="min-w-0 flex-1 pt-0.5">
                <div class="flex flex-wrap items-baseline gap-x-2 gap-y-0.5 mb-1">
                  <span class="font-sans text-[14px] sm:text-[15px] font-semibold text-white">Nfx - switch swapped</span>
                  <span class="font-sans text-[11px] text-text-muted/60">Today at 4:21 PM</span>
                </div>
                <code class="block max-w-full break-words font-mono text-[12px] sm:text-[13.5px] text-accent">/fortnite items: og renegade raider, lvl=100</code>
              </div>
            </div>

            <div class="flex items-start gap-3">
              <img
                src="https://cdn.discordapp.com/icons/1324585061223497842/a_dde93a3b1115dc4f03bac026f50b5611.gif?size=256"
                alt="ClearVault"
                class="w-9 h-9 sm:w-10 sm:h-10 rounded-full object-cover shrink-0"
              />
              <div class="min-w-0 flex-1 pt-0.5">
                <div class="flex flex-wrap items-baseline gap-x-2 gap-y-1 mb-2">
                  <span class="font-sans text-[14px] sm:text-[15px] font-semibold text-white">ClearVault</span>
                  <span class="font-sans text-[10px] font-bold uppercase tracking-wider bg-accent/15 text-accent px-1.5 py-[3px] rounded leading-none">App</span>
                  <span class="font-sans text-[11px] text-text-muted/60">Today at 4:21 PM</span>
                </div>

                <div class="border-l-[4px] border-accent rounded-r bg-secondary/80 p-3 sm:p-4">

                  <div class="flex items-start gap-3 mb-3">
                    <div class="min-w-0 flex-1">
                      <h4 class="font-sans text-[14px] sm:text-[15px] font-semibold text-white leading-tight mb-0.5">Fortnite FA Account</h4>
                      <p class="font-sans text-[11px] sm:text-[12px] text-text-muted">Result 1/9 — Clear Vault Market</p>
                    </div>
                    <img
                      src="https://fortnite-api.com/images/cosmetics/br/cid_028_athena_commando_f/icon.png"
                      alt=""
                      class="w-10 h-10 sm:w-12 sm:h-12 rounded object-cover shrink-0 bg-white/[0.03] border border-white/8"
                    />
                  </div>

                  <div class="mb-3">
                    <p class="font-sans text-[12px] font-semibold text-white mb-0.5">Price</p>
                    <p class="font-sans text-[13px] text-text-muted">$84.00 USD</p>
                  </div>

                  <div class="grid grid-cols-2 gap-3 sm:gap-4 mb-3">
                    <div>
                      <p class="font-sans text-[12px] font-semibold text-white mb-0.5">Inventory</p>
                      <ul class="font-sans text-[12px] sm:text-[12.5px] text-text-muted leading-[1.55]">
                        <li>Skins: 142</li>
                        <li>Pickaxes: 96</li>
                        <li>V-Bucks: 2,400</li>
                      </ul>
                    </div>
                    <div>
                      <p class="font-sans text-[12px] font-semibold text-white mb-0.5">Overview</p>
                      <ul class="font-sans text-[12px] sm:text-[12.5px] text-text-muted leading-[1.55]">
                        <li>Type: FA</li>
                        <li>Level: 187</li>
                        <li>Email Change: No</li>
                      </ul>
                    </div>
                  </div>

                  <div class="mb-4">
                    <p class="font-sans text-[12px] font-semibold text-white mb-0.5">Highlights</p>
                    <p class="font-sans text-[12px] sm:text-[12.5px] text-text-muted">OG Item(s) · Renegade Raider · Black Knight</p>
                  </div>

                  <p class="font-sans text-[10.5px] text-text-muted/60 mb-3">Page 1/9</p>

                  <div class="flex flex-wrap gap-2">
                    <button class="px-2.5 sm:px-3 py-1.5 rounded border border-white/8 bg-white/5 font-sans text-[12px] font-medium text-white">‹ Back</button>
                    <button class="px-2.5 sm:px-3 py-1.5 rounded border border-white/8 bg-white/5 font-sans text-[12px] font-medium text-white">Next ›</button>
                    <button
                      type="button"
                      @click="lockerOpen = true"
                      class="px-2.5 sm:px-3 py-1.5 rounded border border-white/8 bg-white/5 font-sans text-[12px] font-medium text-white transition-colors hover:bg-white/10 cursor-pointer"
                    >
                      Locker
                    </button>
                    <button class="ml-auto px-2.5 sm:px-3 py-1.5 rounded bg-emerald-500 font-sans text-[12px] font-semibold text-black hover:bg-emerald-400">Buy Now</button>
                  </div>
                </div>
              </div>
            </div>

          </div>
        </div>

      </div>
    </div>

    <Teleport to="body">
      <Transition
        enter-active-class="transition-opacity duration-200"
        leave-active-class="transition-opacity duration-200"
        enter-from-class="opacity-0"
        leave-to-class="opacity-0"
      >
        <div
          v-if="lockerOpen"
          class="fixed inset-0 z-[100] flex items-center justify-center p-4 bg-black/85 backdrop-blur-sm cursor-zoom-out"
          @click.self="lockerOpen = false"
          role="dialog"
          aria-modal="true"
        >
          <button
            type="button"
            @click="lockerOpen = false"
            aria-label="Close"
            class="absolute top-5 right-5 w-10 h-10 flex items-center justify-center rounded-full bg-white/10 hover:bg-white/20 text-white transition-colors cursor-pointer"
          >
            <svg class="w-5 h-5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
          <img
            src="/images/locker-preview.webp"
            alt="ClearVault locker preview"
            class="max-w-[calc(100vw-1.5rem)] max-h-[calc(100dvh-1.5rem)] w-auto h-auto rounded-lg shadow-2xl"
            @click.stop
          />
        </div>
      </Transition>
    </Teleport>
  </section>
</template>

<script setup lang="ts">
const lockerOpen = ref(false)

const commands = [
  { cmd: '/market',   title: 'Browse',   desc: 'Search the catalog with filters for skins, level, region, and price.' },
  { cmd: '/topup', title: 'Buy',      desc: 'Generate a checkout invoice and apply any active perks.' },
  { cmd: '/owned',    title: 'Manage',   desc: 'Open past purchases, check warranty, and request refunds.' },
  { cmd: '/staffview',title: 'Refunds',  desc: 'Hand a single order to ranked staff for refund review without giving up account access.' },
]

onMounted(() => {
  const onKey = (e: KeyboardEvent) => {
    if (e.key === 'Escape') lockerOpen.value = false
  }
  window.addEventListener('keydown', onKey)
  onBeforeUnmount(() => window.removeEventListener('keydown', onKey))
})
</script>
