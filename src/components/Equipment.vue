<script setup>
import dispensador_4_mangueras from '@/assets/images/dispensador_4_mangeras.png'
import surtidor_urea from '@/assets/images/surtidor_urea.png'
import dispensador_auto_glp from '@/assets/images/dispensador_auto_glp.png'
import equipo_bajo_perfil from '@/assets/images/equipo_bajo_perfil.png'

const products = [
  {
    name: 'Dispensador 4 Mangueras',
    description:
      'Sistema avanzado de detección para tanques y tuberías con análisis forense de alta precisión.',
    brand: 'Bluesky®',
    imageUrl: dispensador_4_mangueras,
  },
  {
    name: 'Surtidor de Urea',
    brand: 'Bluesky®',
    imageUrl: surtidor_urea,
  },
  {
    name: 'Dispensador Auto GLP',
    brand: 'Bluesky®',
    imageUrl: dispensador_auto_glp,
  },
  {
    name: 'Equipo bajo perfil',
    brand: 'Bluesky®',
    imageUrl: equipo_bajo_perfil,
  },
]
</script>

<template>
  <section
    id="equipos"
    aria-label="Equipos de élite Petrofix"
    class="bg-[#050810] py-20 sm:py-28 lg:py-32"
  >
    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-12">
      <!-- Header -->
      <div class="mb-16 sm:mb-20 flex flex-col gap-8 md:flex-row md:items-end md:justify-between">
        <h2
          class="max-w-2xl text-4xl sm:text-6xl lg:text-7xl
                 font-black uppercase tracking-tighter
                 text-white leading-[0.95]"
        >
          EQUIPOS DE <br />
          <span class="text-orange-500 italic">ÉLITE</span>.
        </h2>
      </div>

      <!-- Grid -->
      <div class="grid grid-cols-1 gap-6 md:grid-cols-12">
        <!-- PRODUCTO PRINCIPAL -->
        <div
          class="group relative overflow-hidden
                 rounded-[3rem]
                 border border-white/10
                 md:col-span-8
                 h-[420px] sm:h-[520px] lg:h-[600px]
                 shadow-2xl"
        >
          <img
            :src="products[0].imageUrl"
            :alt="products[0].name"
            loading="lazy"
            class="absolute  h-full w-full
                   object-cover
                   scale-80
                   brightness-90 contrast-90 saturate-90
                   transition-transform duration-700
                   group-hover:scale-115"
          />

          <!-- Overlay principal -->
          <div
            class="absolute inset-0
                   bg-gradient-to-t
                   from-black/80 via-black/30 to-transparent"
          ></div>

          <!-- Content -->
          <div class="absolute bottom-0 left-0 z-10 p-6 sm:p-10 lg:p-12">
            <h3
              class="mb-4 text-3xl sm:text-4xl lg:text-5xl
                     font-black uppercase tracking-tighter text-white"
            >
              {{ products[0].name }}
            </h3>

            <p
              class="mb-8 max-w-md
                     text-base sm:text-lg
                     font-medium text-slate-300"
            >
              {{ products[0].description }}
            </p>

            <button
              class="flex items-center gap-3
                     rounded-xl bg-white
                     px-8 py-4
                     font-black uppercase text-black
                     transition-all
                     hover:bg-orange-500 hover:text-white
                     active:scale-95"
            >
              Solicitar ficha técnica
              <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor">
                <path d="M12 5v14M5 12h14" stroke="currentColor" stroke-width="2"/>
              </svg>
            </button>
          </div>
        </div>

        <!-- PRODUCTOS SECUNDARIOS -->
        <div class="flex flex-col gap-6 md:col-span-4">
          <div
            v-for="(product, index) in products.slice(1)"
            :key="index"
            class="group relative flex-1 overflow-hidden
                   rounded-[1rem]
                   border border-white/10
                   min-h-[240px] sm:min-h-[280px]"
          >
            <img
              :src="product.imageUrl"
              :alt="product.name"
              loading="lazy"
              class="absolute inset-0 h-full w-full
                     object-cover
                     scale-105
                     brightness-90 contrast-100 saturate-95
                     opacity-85
                     transition-all duration-700
                     group-hover:opacity-100
                     group-hover:scale-115
                     group-hover:brightness-125"
            />

            <!-- Overlay secundario -->
            <div class="absolute inset-0 bg-black/40"></div>

            <div class="relative z-10 p-6 sm:p-8">
              <h4
                class="mb-2 text-xl sm:text-2xl
                       font-black uppercase text-white"
              >
                {{ product.name }}
              </h4>

              <p
                class="text-xs font-black uppercase tracking-widest
                       text-orange-500"
              >
                {{ product.brand }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
