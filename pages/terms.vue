<template>
  <div>
    <section class="relative pt-20 pb-0 overflow-hidden">
      <div aria-hidden="true" class="absolute inset-0 -z-10 grid grid-cols-2 -space-x-52 opacity-[0.08]">
        <div class="h-48 bg-gradient-to-br from-accent to-[#ff6b6b] blur-[100px]" />
        <div class="h-28 bg-gradient-to-r from-accent-secondary to-accent blur-[100px]" />
      </div>

      <div class="relative z-10 max-w-7xl mx-auto px-6 md:px-12">
        <div class="text-center max-w-lg mx-auto mb-14">
          <h1 class="font-[Syne] text-4xl md:text-5xl font-extrabold text-white mb-4 leading-[1.1]">Terms of Service</h1>
          <p class="font-sans text-[15px] text-text-muted leading-relaxed">By purchasing from Xmarket, you agree to these terms, which govern the sale of digital products through our Discord server.</p>
          <p class="font-sans text-xs text-text-muted/40 mt-4">Effective from the date of your first purchase.</p>
        </div>
      </div>
    </section>

    <div class="max-w-7xl mx-auto px-6 md:px-12 pb-16">
      <div class="max-w-4xl mx-auto space-y-3">
        <div
          v-for="section in sections"
          :key="section.num"
          class="rounded-2xl border border-white/6 bg-surface overflow-hidden"
        >
          <button
            @click="toggleSection(section.num)"
            class="w-full flex items-center justify-between p-6 text-left transition-colors hover:bg-white/2"
          >
            <div class="flex items-center gap-4">
              <span class="font-[Syne] text-sm font-bold text-accent w-8 shrink-0">{{ section.num }}</span>
              <h3 class="font-[Syne] text-base font-bold text-white">{{ section.title }}</h3>
            </div>
            <svg
              class="w-4 h-4 text-text-muted transition-transform duration-200 shrink-0 ml-4"
              :class="openSections.includes(section.num) ? 'rotate-180' : ''"
              fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="1.5"
            >
              <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 8.25l-7.5 7.5-7.5-7.5" />
            </svg>
          </button>
          <div class="faq-content" :class="openSections.includes(section.num) ? 'is-open' : ''">
            <div>
              <div class="px-6 pb-6 ml-12 space-y-2.5 border-l border-white/6 pl-5">
                <p
                  v-for="(clause, i) in section.clauses"
                  :key="i"
                  class="font-sans text-sm text-text-muted leading-relaxed"
                >{{ clause }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="max-w-7xl mx-auto px-6 md:px-12 pb-24">
      <div class="max-w-4xl mx-auto">
        <div class="rounded-2xl border border-white/6 bg-surface p-8">
          <div class="flex items-start gap-4 mb-8">
            <div class="w-10 h-10 rounded-xl bg-accent/10 border border-accent/20 flex items-center justify-center shrink-0">
              <svg class="w-5 h-5 text-accent" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="1.5">
                <path stroke-linecap="round" stroke-linejoin="round" d="M9.879 7.519c1.171-1.025 3.071-1.025 4.242 0 1.172 1.025 1.172 2.687 0 3.712-.203.179-.43.326-.67.442-.745.361-1.45.999-1.45 1.827v.75M21 12a9 9 0 11-18 0 9 9 0 0118 0zm-9 5.25h.008v.008H12v-.008z" />
              </svg>
            </div>
            <div>
              <h2 class="font-[Syne] text-xl font-bold text-white mb-1">Have a question or issue?</h2>
              <p class="font-sans text-sm text-text-muted leading-relaxed">Select your issue type to see the relevant policy and what to do next.</p>
            </div>
          </div>

          <div class="flex flex-wrap gap-2 mb-6">
            <button
              v-for="issue in issueTypes"
              :key="issue.id"
              @click="selectedIssue = selectedIssue === issue.id ? null : issue.id"
              class="flex items-center gap-2 px-4 py-2 rounded-xl font-sans text-sm font-semibold border transition-all duration-200"
              :class="selectedIssue === issue.id
                ? 'bg-accent/10 border-accent/30 text-accent'
                : 'border-white/8 text-text-muted hover:text-white hover:border-white/15'"
            >
              <svg class="w-3.5 h-3.5 shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="1.5">
                <path stroke-linecap="round" stroke-linejoin="round" :d="issue.icon" />
              </svg>
              {{ issue.label }}
            </button>
          </div>

          <Transition
            enter-active-class="transition-all duration-300 ease-out"
            enter-from-class="opacity-0 translate-y-2"
            enter-to-class="opacity-100 translate-y-0"
            leave-active-class="transition-all duration-200 ease-in"
            leave-from-class="opacity-100"
            leave-to-class="opacity-0"
            mode="out-in"
          >
            <div v-if="currentIssue" :key="currentIssue.id" class="rounded-xl border border-white/8 bg-secondary p-6">
              <p class="font-sans text-[10px] font-bold uppercase tracking-widest text-accent mb-2">Relevant Policy</p>
              <h4 class="font-[Syne] text-base font-bold text-white mb-3">{{ currentIssue.title }}</h4>
              <p class="font-sans text-sm text-text-muted leading-relaxed mb-4">{{ currentIssue.content }}</p>
              <div v-if="currentIssue.steps" class="mb-5">
                <p class="font-sans text-xs font-semibold text-white mb-2.5">What to do:</p>
                <ol class="space-y-2">
                  <li v-for="(step, i) in currentIssue.steps" :key="i" class="flex items-start gap-2.5">
                    <span class="font-[Syne] text-xs font-bold w-5 h-5 rounded-full bg-accent/20 text-accent flex items-center justify-center shrink-0 mt-0.5">{{ i + 1 }}</span>
                    <p class="font-sans text-xs text-text-muted leading-relaxed">{{ step }}</p>
                  </li>
                </ol>
              </div>
              <a
                href="https://discord.gg/bnhwFSU75P"
                target="_blank"
                rel="noopener noreferrer"
                class="inline-flex items-center gap-2 px-5 py-2.5 rounded-xl bg-accent font-sans text-sm font-semibold text-background transition-colors duration-200 hover:bg-accent/90"
              >
                <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="1.5">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M20.25 8.511c.884.284 1.5 1.128 1.5 2.097v4.286c0 1.136-.847 2.1-1.98 2.193-.34.027-.68.052-1.02.072v3.091l-3-3c-1.354 0-2.694-.055-4.02-.163a2.115 2.115 0 01-.825-.242m9.345-8.334a2.126 2.126 0 00-.476-.095 48.64 48.64 0 00-8.048 0c-1.131.094-1.976 1.057-1.976 2.192v4.286c0 .837.46 1.58 1.155 1.951m9.345-8.334V6.637c0-1.621-1.152-3.026-2.76-3.235A48.455 48.455 0 0011.25 3c-2.115 0-4.198.137-6.24.402-1.608.209-2.76 1.614-2.76 3.235v6.226c0 1.621 1.152 3.026 2.76 3.235.577.075 1.157.14 1.74.194V21l4.155-4.155" />
                </svg>
                Contact Support on Discord
              </a>
            </div>
          </Transition>

          <div v-if="!selectedIssue" class="rounded-xl border border-white/6 bg-secondary/50 p-5 flex items-center gap-4">
            <svg class="w-5 h-5 text-text-muted/50 shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="1.5">
              <path stroke-linecap="round" stroke-linejoin="round" d="M15.182 15.182a4.5 4.5 0 01-6.364 0M21 12a9 9 0 11-18 0 9 9 0 0118 0zM9.75 9.75c0 .414-.168.75-.375.75S9 10.164 9 9.75 9.168 9 9.375 9s.375.336.375.75zm-.375 0h.008v.015h-.008V9.75zm5.625 0c0 .414-.168.75-.375.75s-.375-.336-.375-.75.168-.75.375-.75.375.336.375.75zm-.375 0h.008v.015h-.008V9.75z" />
            </svg>
            <p class="font-sans text-sm text-text-muted/60">Select an issue type above and we'll show you what to do.</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
useSeoMeta({
  title: 'Terms of Service — Xmarket',
  ogTitle: 'Xmarket Terms of Service',
  description: 'By purchasing from Xmarket, you agree to these terms, which govern the sale of digital products through our Discord server.',
  ogDescription: 'By purchasing from Xmarket, you agree to these terms, which govern the sale of digital products through our Discord server.',
})

const openSections = ref<string[]>(['1'])

function toggleSection(num: string) {
  const idx = openSections.value.indexOf(num)
  if (idx === -1) openSections.value.push(num)
  else openSections.value.splice(idx, 1)
}

const sections = [
  {
    num: '1',
    title: 'Introduction',
    clauses: [
      'By purchasing from Xmarket, you agree to these Terms of Service (TOS), which govern the sale of Fortnite, Steam, VPNs, and related digital products.',
    ],
  },
  {
    num: '2',
    title: 'Product Sales',
    clauses: [
      '2.1. Xmarket sells digital products sourced from third-party providers. We do not knowingly offer unauthorized or illegitimate products.',
      '2.2. Market Access: Use /fortnite for Fortnite products and /market for others. Commands are private.',
      '2.3. Accurate Information: Ensure you review product details before purchase to confirm suitability and compliance with platform terms.',
    ],
  },
  {
    num: '3',
    title: 'Warranty Policy',
    clauses: [
      '3.1. Warranty Duration: Xmarket offers a 24-hour warranty for technical support and product functionality.',
      '3.2. Scope: Warranty covers non-functional product data. Replacements are provided within the warranty period.',
      '3.3. Exclusions: Warranty is void if details are shared, changes are made after delivery, or cheats are used.',
      '3.4. Post-Warranty: Xmarket is not responsible for issues arising from platform policy changes or user actions after the warranty period.',
    ],
  },
  {
    num: '4',
    title: 'Refund Policy',
    clauses: [
      '4.1. Refunds are not issued for user actions after purchase.',
      '4.2. Eligibility: Refunds are provided if the product does not function as described and must be requested within the warranty period.',
      '4.3. Access Revocation: Refunds for products where access has been revoked by the issuing platform require no modifications to access details and must be requested within 24 hours of the revocation.',
      '4.4. Final Sale: All sales are final unless covered under warranty.',
      '4.5. Refund Method: Refunds are credited back to your balance at Xmarket. Only rare exceptions will be made for refunds back to card or crypto.',
      '4.6. Refund Exclusion for Epic Games Issues: In cases where product issues are directly attributable to Epic Games platform malfunctions, no refunds will be issued. Buyers acknowledge that such issues are beyond Xmarket\'s control.',
      '4.7. Evidence Requirement: To be eligible for a refund, the buyer must provide clear video evidence showing the purchase and attempted use of the digital item, as well as the issue encountered. Without this video evidence, refund requests may be rejected.',
      '4.8. Minimum Value Restriction: No refunds will be issued for products valued under $1, regardless of circumstances.',
    ],
  },
  {
    num: '5',
    title: 'Product Risks',
    clauses: [
      '5.1. Xmarket does not guarantee product longevity due to potential third-party platform changes.',
      '5.2. Security beyond seven days is not guaranteed.',
      '5.3. Data Loss and Backups: Due to the nature of this service, Xmarket does not maintain backups of purchased product data. It is the sole responsibility of the buyer to export and store their product data immediately after purchase.',
    ],
  },
  {
    num: '6',
    title: 'Prohibited Activities',
    clauses: [
      '6.1. Misuse: Xmarket products must be used in accordance with the applicable platform or service\'s user guidelines, for which Xmarket assumes no liability.',
      '6.2. Tournament Participation: Certain products are not intended for use in competitive or ranked environments. Doing so may lead to suspension by the issuing platform and is not covered under warranty.',
    ],
  },
  {
    num: '7',
    title: 'Support & Assistance',
    clauses: [
      '7.1. Help: Visit the Command Help channel for assistance and guides: discord.gg/bnhwFSU75P',
      '7.2. Response Times: Support inquiries are addressed within 24 hours, subject to availability.',
    ],
  },
  {
    num: '8',
    title: 'Limitation of Liability',
    clauses: [
      '8.1. Warranty Limits: Xmarket\'s liability is limited to the terms of the warranty and refund policy.',
      '8.2. Xmarket is not responsible for third-party platform changes affecting product functionality.',
      '8.3. Indemnification: Buyers agree to indemnify and hold Xmarket harmless from claims arising from misuse or unauthorized use of purchased products.',
      '8.4. Server Downtime: Xmarket is not liable for any financial or data loss incurred if the service or its servers become unavailable.',
    ],
  },
  {
    num: '9',
    title: 'Amendments to TOS',
    clauses: [
      '9.1. Updates: Xmarket may update these Terms of Service at any time.',
      '9.2. Acceptance: Continued use or purchases imply acceptance of updated terms.',
    ],
  },
  {
    num: '10',
    title: 'Giveaway Terms',
    clauses: [
      '10.1. No Warranties: All products distributed via giveaways or free promotions are provided "AS IS." Xmarket offers no warranty or technical support for giveaway items.',
      '10.2. No Replacements: Giveaway items are not eligible for replacements or credits if the product is non-functional or revoked.',
      '10.3. Discretion: Xmarket reserves the right to cancel giveaways or disqualify participants at its sole discretion.',
    ],
  },
  {
    num: '11',
    title: 'Acceptance of Terms',
    clauses: [
      'By purchasing from Xmarket, you acknowledge that you have read, understood, and agree to these Terms of Service, including the risks and limitations stated.',
    ],
  },
]

const selectedIssue = ref<string | null>(null)

const issueTypes = [
  {
    id: 'refund',
    label: 'Refund Request',
    icon: 'M2.25 8.25h19.5M2.25 9h19.5m-16.5 5.25h6m-6 2.25h3m-3.75 3h15a2.25 2.25 0 002.25-2.25V6.75A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25v10.5A2.25 2.25 0 004.5 19.5z',
    title: 'Refund Policy (Section 4)',
    content: 'Refunds are only available within the 24-hour warranty window if your product was pulled, login failed, or was banned on purchase. All refunds are credited back to your Xmarket balance.',
    steps: [
      'Run /owned and select your account.',
      'If warranty is still active, press the Refund Button.',
      'Provide your reason (pulled / banned) and an unlisted YouTube video showing the issue.',
      'Our team will review within 24 hours.',
    ],
  },
  {
    id: 'warranty',
    label: 'Warranty Question',
    icon: 'M9 12.75L11.25 15 15 9.75m-3-7.036A11.959 11.959 0 013.598 6 11.99 11.99 0 003 9.749c0 5.592 3.824 10.29 9 11.623 5.176-1.332 9-6.03 9-11.622 0-1.31-.21-2.571-.598-3.751h-.152c-3.196 0-6.1-1.248-8.25-3.285z',
    title: 'Warranty Policy (Section 3)',
    content: 'Xmarket offers a 24-hour warranty covering non-functional product data. Warranty is void if you share account details, make changes after delivery, or use cheats. After 24 hours, Xmarket is not liable for platform-side changes.',
    steps: [
      'Check /owned immediately after purchase to verify your product works.',
      'If there is an issue within 24 hours, open a support ticket on Discord.',
      'Provide your order details and a video showing the problem.',
    ],
  },
  {
    id: 'account',
    label: 'Account Pulled / Banned',
    icon: 'M18.364 18.364A9 9 0 005.636 5.636m12.728 12.728A9 9 0 015.636 5.636m12.728 12.728L5.636 5.636',
    title: 'Access Revocation (Section 4.3)',
    content: 'If your product\'s access was revoked by the issuing platform, you must request a refund within 24 hours. No modifications to account details should have been made after delivery for this to be eligible.',
    steps: [
      'Do not make any changes to the account.',
      'Run /owned and press Refund if within warranty.',
      'Provide an unlisted YouTube video as proof of the revocation.',
    ],
  },
  {
    id: 'tournament',
    label: 'Tournament / Competitive',
    icon: 'M16.5 18.75h-9m9 0a3 3 0 013 3h-15a3 3 0 013-3m9 0v-3.375c0-.621-.503-1.125-1.125-1.125h-.871M7.5 18.75v-3.375c0-.621.504-1.125 1.125-1.125h.872m5.007 0H9.497m5.007 0a7.454 7.454 0 01-.982-3.172M9.497 14.25a7.454 7.454 0 00.981-3.172M5.25 4.236c-.982.143-1.954.317-2.916.52A6.003 6.003 0 007.73 9.728M5.25 4.236V4.5c0 2.108.966 3.99 2.48 5.228M5.25 4.236V2.721C7.456 2.41 9.71 2.25 12 2.25c2.291 0 4.545.16 6.75.47v1.516M7.73 9.728a6.726 6.726 0 002.748 1.35m8.272-6.842V4.5c0 2.108-.966 3.99-2.48 5.228m2.48-5.492a46.32 46.32 0 012.916.52 6.003 6.003 0 01-5.395 4.972m0 0a6.726 6.726 0 01-2.749 1.35m0 0a6.772 6.772 0 01-3.044 0',
    title: 'Prohibited Activities (Section 6.2)',
    content: 'Products not labeled as tournament-ready are not covered if used in competitive or ranked events. If your product gets suspended due to competitive use without the tready label, this is not covered under warranty.',
    steps: [
      'Use the tready filter command in the marketplace to find eligible products.',
      'Only enter competitive modes with accounts specifically labeled as tournament-ready.',
    ],
  },
  {
    id: 'giveaway',
    label: 'Giveaway Item',
    icon: 'M21 11.25v8.25a1.5 1.5 0 01-1.5 1.5H5.25a1.5 1.5 0 01-1.5-1.5v-8.25M12 4.875A2.625 2.625 0 109.375 7.5H12m0-2.625V7.5m0-2.625A2.625 2.625 0 1114.625 7.5H12m0 0V21m-8.625-9.75h18c.621 0 1.125-.504 1.125-1.125v-1.5c0-.621-.504-1.125-1.125-1.125h-18c-.621 0-1.125.504-1.125 1.125v1.5c0 .621.504 1.125 1.125 1.125z',
    title: 'Giveaway Terms (Section 10)',
    content: 'All giveaway products are provided "AS IS" with no warranty. They are not eligible for replacements or credits if non-functional or revoked. Xmarket may cancel giveaways or disqualify participants at its discretion.',
    steps: [
      'Giveaway items have no warranty coverage — this is by design.',
      'If you have a question, you can still reach out on Discord but replacements are not guaranteed.',
    ],
  },
]

const currentIssue = computed(() => issueTypes.find(i => i.id === selectedIssue.value) ?? null)
</script>
