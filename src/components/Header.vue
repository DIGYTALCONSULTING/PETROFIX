<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import logo from '@/assets/images/logo.png'

const isOpen = ref(false)
const isScrolled = ref(false)

const navItems = [
  { label: 'Inicio', href: '#inicio' },
  { label: 'Servicios', href: '#servicios' },
  { label: 'Productos', href: '#productos' },
  { label: 'Accesorios', href: '#accesorios' },
]

const cta = {
  label: 'Iniciar proyecto',
  href: '#contacto',
}

const onScroll = () => {
  isScrolled.value = window.scrollY > 50
}

onMounted(() => {
  window.addEventListener('scroll', onScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', onScroll)
})
</script>

<template>
  <header
    class="fixed top-0 z-50 w-full transition-all duration-300"
    :class="isScrolled ? 'bg-black/80 backdrop-blur border-b border-white/10 py-3' : 'bg-transparent py-5'"
  >
    <div class="mx-auto max-w-7xl px-4">
      <div class="flex items-center justify-between">

        <!-- LOGO -->
        <a href="#inicio" class="flex items-center gap-3">
          <img :src="logo" alt="Petrofix" class="
              h-11 sm:h-12 lg:h-14
              w-auto
              drop-shadow-[0_0_2px_#ffffff]
              transition-all duration-300 hover:drop-shadow-[0_0_6px_#ffffff]
            " />
          <span class="text-lg font-black uppercase tracking-tight text-white">
            PETRO<span class="text-orange-500">FIX</span>
          </span>
        </a>

        <!-- NAV DESKTOP -->
        <nav class="hidden items-center gap-8 lg:flex">
          <a
            v-for="item in navItems"
            :key="item.href"
            :href="item.href"
            class="text-xs font-bold uppercase tracking-widest text-gray-300 hover:text-white transition"
          >
            {{ item.label }}
          </a>

          <!-- BOTÓN CTA -->
          <a
            :href="cta.href"
            class="rounded-xl bg-orange-600 px-6 py-2.5
                   text-xs font-bold uppercase tracking-widest text-white
                   hover:bg-orange-700 transition"
          >
            {{ cta.label }}
          </a>
        </nav>

        <!-- BOTÓN MOBILE -->
        <button
          class="text-white lg:hidden"
          @click="isOpen = !isOpen"
          aria-label="Abrir menú"
        >
          ☰
        </button>
      </div>

      <!-- NAV MOBILE -->
      <div v-if="isOpen" class="mt-4 space-y-4 lg:hidden">
        <a
          v-for="item in navItems"
          :key="item.href"
          :href="item.href"
          class="block text-sm font-bold uppercase text-gray-300"
          @click="isOpen = false"
        >
          {{ item.label }}
        </a>

        <!-- CTA MOBILE -->
        <a
          :href="cta.href"
          class="block rounded-xl bg-orange-600 py-3
                 text-center text-xs font-bold uppercase tracking-widest
                 text-white hover:bg-orange-700 transition"
          @click="isOpen = false"
        >
          {{ cta.label }}
        </a>
      </div>
    </div>
  </header>
</template>
