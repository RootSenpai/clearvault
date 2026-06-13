<template>
  <section id="home" class="relative min-h-[90vh] flex items-center overflow-hidden">

    <div aria-hidden="true" class="absolute inset-0 grid grid-cols-2 -space-x-52 opacity-[0.12]">
      <div class="h-56 bg-gradient-to-br from-accent to-[#ff6b6b] blur-[106px]" />
      <div class="h-32 bg-gradient-to-r from-accent-secondary to-accent blur-[106px]" />
    </div>

    <img
      aria-hidden="true"
      src="https://fortnite-api.com/images/cosmetics/br/character_quichelorrainelime/featured.png"
      alt=""
      class="absolute bottom-0 -left-4 h-auto max-h-[38vh] w-[42vw] max-w-[11rem] object-contain object-bottom opacity-20 sm:left-2 sm:h-[55vh] sm:max-h-none sm:w-auto sm:max-w-none sm:opacity-40 md:left-6 md:h-[65vh] lg:left-10 xl:h-[78vh] select-none pointer-events-none"
      style="mask-image: linear-gradient(to top, transparent 0%, black 25%); -webkit-mask-image: linear-gradient(to top, transparent 0%, black 25%);"
    />

    <img
      aria-hidden="true"
      src="https://media.valorant-api.com/agents/add6443a-41bd-e414-f6ad-e58d267f4e95/fullportrait.png"
      alt=""
      class="absolute bottom-0 -right-4 h-auto max-h-[40vh] w-[42vw] max-w-[11rem] object-contain object-bottom opacity-20 sm:right-2 sm:h-[58vh] sm:max-h-none sm:w-auto sm:max-w-none sm:opacity-40 md:right-6 md:h-[68vh] lg:right-10 xl:h-[82vh] select-none pointer-events-none"
      style="mask-image: linear-gradient(to top, transparent 0%, black 25%); -webkit-mask-image: linear-gradient(to top, transparent 0%, black 25%);"
    />

    <div class="relative z-10 mx-auto max-w-7xl px-6 md:px-12 w-full">
      <div class="mx-auto text-center lg:w-2/3 pt-12">

        <h1 class="font-[Syne] text-5xl font-bold text-white md:text-6xl xl:text-7xl anim-text-focus-in">
          Your secure marketplace for
          <span class="gradient-text"> gaming accounts.</span>
        </h1>

        <p class="mt-8 font-sans text-lg text-text-muted anim-fade-in-bottom" style="animation-delay: 0.6s">
          Browse, checkout, and manage digital products — all from within the Xmarket Discord server.
        </p>

        <div class="mt-12 flex flex-wrap justify-center gap-4 anim-fade-in-bottom" style="animation-delay: 0.9s">
          <a
            href="https://discord.gg/bnhwFSU75P"
            target="_blank"
            rel="noopener noreferrer"
            class="flex h-11 items-center justify-center rounded-full bg-accent px-8 font-sans text-sm font-semibold text-background transition-colors duration-200 hover:bg-accent/90"
          >
            Join Xmarket
          </a>
          <a
            href="#commands"
            class="flex h-11 items-center justify-center px-8 rounded-full border border-white/10 bg-white/5 font-sans text-sm font-semibold text-white transition-colors duration-200 hover:bg-white/10"
          >
            View Commands
          </a>
        </div>

        <div class="grid grid-cols-4 gap-2 mt-16 pt-8 border-t border-border anim-fade-in-bottom" style="animation-delay: 1.1s">
          <div v-for="stat in stats" :key="stat.value">
            <div class="font-[Syne] text-2xl font-bold text-white mb-1">{{ stat.value }}</div>
            <div class="font-sans text-xs text-text-muted leading-snug">{{ stat.label }}</div>
          </div>
        </div>

      </div>
    </div>

  </section>
</template>

<script setup lang="ts">
const stats = [
  { value: '24/7', label: 'Discord delivery' },
  { value: '6+',   label: 'Service categories' },
  { value: '24h',  label: 'Warranty window' },
  { value: 'Live', label: 'Support tools' },
]
</script>
