<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

import swivelImg from '@/assets/images/swivwl_certificado.webp'
import breakawayImg from '@/assets/images/breakway_certificado.webp'
import mangueraImg from '@/assets/images/mangueras_certificada.webp'
import serafin5Img from '@/assets/images/serafin_5galones.webp'
import serafin05Img from '@/assets/images/serafin_05_galones.webp'
import pistolasImg from '@/assets/images/pistolas_de_combustible.webp'

const sectionRef = ref(null)
const hasAnimated = ref(false)

let observer = null

onMounted(() => {
  observer = new IntersectionObserver(
    ([entry]) => {
      if (entry.isIntersecting) {
        hasAnimated.value = true
      }
    },
    { threshold: 0.2 }
  )

  if (sectionRef.value) observer.observe(sectionRef.value)
})

onBeforeUnmount(() => {
  if (observer && sectionRef.value) observer.unobserve(sectionRef.value)
})

const accesorios = [
  { name: 'Swivel certificado', image: swivelImg },
  { name: 'Breakaway certificado', image: breakawayImg },
  { name: 'Mangueras con alma de acero certificada', image: mangueraImg },
  { name: 'Serafín de 5 galones', image: serafin5Img },
  { name: 'Serafín de 0.5 galones', image: serafin05Img },
  { name: 'Pistolas de combustible', image: pistolasImg }
]
</script>

<template>
  <section
    ref="sectionRef"
    id="accesorios"
    aria-labelledby="accesorios-title"
    class="relative bg-[#050810] py-28 overflow-hidden"
  >
    <!-- Glow ambiental -->
    <div class="pointer-events-none absolute -bottom-40 left-1/2 h-[500px] w-[500px] -translate-x-1/2 rounded-full bg-orange-500/10 blur-[180px]"></div>

    <div class="relative z-10 mx-auto max-w-7xl px-6">

      <!-- HEADER -->
      <header
        class="mb-24 text-center transition-all duration-1000 ease-out"
        :class="hasAnimated ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'"
      >
        <h2
          id="accesorios-title"
          class="text-5xl md:text-6xl font-black uppercase tracking-tight text-white"
        >
          ACCESORIOS
          <span class="text-blue-500 italic"> CERTIFICADOS</span>
        </h2>

        <div class="mx-auto mt-6 h-[2px] w-24 bg-gradient-to-r from-transparent via-orange-500 to-transparent"></div>

        <p class="mt-8 max-w-3xl mx-auto text-slate-400 text-lg leading-relaxed">
          Venta de repuestos y accesorios certificados para estaciones de servicio,
          garantizando seguridad operativa, precisión técnica y cumplimiento normativo internacional.
        </p>
      </header>

      <!-- GRID -->
      <div class="grid grid-cols-1 gap-10 sm:grid-cols-2 lg:grid-cols-3">

        <article
          v-for="(item, index) in accesorios"
          :key="index"
          class="group relative rounded-[2rem] bg-gradient-to-br from-[#0c111c] to-[#050810] border border-white/10 p-10 text-center shadow-xl transition-all duration-1000 ease-out hover:-translate-y-4 hover:border-orange-500/40"
          :class="hasAnimated ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'"
          :style="{ transitionDelay: `${index * 120}ms` }"
        >

          <!-- Imagen -->
          <div class="mb-8 flex items-center justify-center h-54">
            <img
              :src="item.image"
              :alt="item.name"
              class="max-h-full object-contain transition-transform duration-700 group-hover:scale-110"
              loading="lazy"
            />
          </div>

          <!-- Nombre -->
          <h3 class="text-lg font-bold uppercase tracking-wide text-white">
            {{ item.name }}
          </h3>

          <!-- Línea animada -->
          <div class="mt-4 h-[2px] w-10 bg-blue-500 transition-all duration-500 group-hover:w-16 mx-auto"></div>

        </article>

      </div>

    </div>
  </section>
</template>
