<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import dispensador_4_mangueras from '@/assets/images/dispensador_4_mangeras.png'
import surtidor_urea from '@/assets/images/surtidor_urea.png'
import dispensador_auto_glp from '@/assets/images/dispensador_auto_glp.png'
import equipo_bajo_perfil from '@/assets/images/equipo_bajo_perfil.png'

const sectionRef = ref(null)
const hasAnimated = ref(false)
const buttonRef = ref(null)

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

  if (sectionRef.value) {
    observer.observe(sectionRef.value)
  }
})

onBeforeUnmount(() => {
  if (observer && sectionRef.value) {
    observer.unobserve(sectionRef.value)
  }
})

function handleMagnet(e) {
  const btn = buttonRef.value
  if (!btn) return

  const rect = btn.getBoundingClientRect()
  const x = e.clientX - rect.left - rect.width / 2
  const y = e.clientY - rect.top - rect.height / 2

  btn.style.transform = `translate(${x * 0.2}px, ${y * 0.2}px)`
}

function resetMagnet() {
  if (buttonRef.value) {
    buttonRef.value.style.transform = `translate(0px, 0px)`
  }
}

const products = [
  {
    name: 'Dispensador 4 Mangueras',
    description:
      'Sistema profesional de despacho simultáneo con alta precisión de medición, ideal para estaciones de servicio que requieren rendimiento, confiabilidad y tecnología certificada.',
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
    ref="sectionRef"
    id="equipos"
    aria-labelledby="equipos-title"
    class="bg-[#050810] py-24 overflow-hidden"
  >
    <div class="mx-auto max-w-7xl px-6">

      <!-- HEADER SEO -->
      <header
        class="mb-20 transition-all duration-1000 ease-out"
        :class="hasAnimated ? 'opacity-100 translate-y-0' : 'opacity-90 translate-y-6'"
      >
        <h2
          id="equipos-title"
          class="text-5xl md:text-6xl font-black uppercase text-white leading-[0.95]"
        >
          SURTIDORES Y
          <span class="text-blue-500 italic"> DISPENSADORES.</span>
        </h2>

        <!-- Línea decorativa -->
        <div class="mt-6 h-[3px] w-28 bg-gradient-to-r from-transparent via-blue-500 to-transparent"></div>

        <!-- Descripción SEO -->
        <p class="mt-8 max-w-3xl text-slate-400 leading-relaxed text-lg">
          Distribuidores exclusivos en Colombia de dispensadores y surtidores 
          <strong class="text-white">Bluesky Energy and Technology</strong>, 
          diseñados para ofrecer máxima precisión, alto rendimiento y cumplimiento 
          de estándares técnicos certificados para estaciones de servicio modernas.
        </p>
      </header>

      <div class="grid grid-cols-1 gap-10 md:grid-cols-12">

        <!-- PRINCIPAL -->
        <article
          class="group relative md:col-span-8 rounded-[2.5rem] bg-gradient-to-br from-[#0c111c] to-[#050810] border border-white/10 shadow-2xl transition-all duration-1000 ease-out overflow-hidden"
          :class="hasAnimated ? 'opacity-100 translate-y-0' : 'opacity-95 translate-y-8'"
        >

          <div class="absolute inset-0 bg-[radial-gradient(circle_at_center,rgba(59,130,246,0.08),transparent_70%)]"></div>

          <!-- Imagen -->
          <div class="relative h-[460px] md:h-[520px] flex items-center justify-center p-10 md:p-14">
            <img
              :src="products[0].imageUrl"
              :alt="products[0].name"
              class="max-h-full max-w-full object-contain transition-transform duration-700 group-hover:scale-105"
              loading="lazy"
            />
          </div>

          <!-- Contenido -->
          <div class="relative z-10 px-8 md:px-14 pb-14">

            <h3 class="text-3xl md:text-5xl font-black uppercase text-white mb-6">
              {{ products[0].name }}
            </h3>

            <p class="text-slate-400 mb-10 max-w-2xl leading-relaxed">
              {{ products[0].description }}
            </p>

            <!-- Lista técnica optimizada SEO -->
            <ul class="grid grid-cols-1 md:grid-cols-2 gap-x-10 gap-y-4 text-slate-300 text-sm md:text-base leading-relaxed mb-12">
              <li>• Despacho simultáneo por cada manguera.</li>
              <li>• Flujo estándar de 12 a 16 GMP.</li>
              <li>• Alta entrega de 12 a 16 GMP.</li>
              <li>• Motor eléctrico 1.0 HP 220V certificado a prueba de explosión.</li>
              <li>• Computador electrónico independiente por equipo.</li>
              <li>• Voltaje 220V - 60Hz.</li>
              <li>• Precisión certificada de ±0.3%.</li>
              <li>• Guarda hasta 50 ventas por manguera.</li>
              <li>• Display de 8 dígitos (más de 10.000.000 por tanqueo).</li>
              <li>• 6 PPU configurables.</li>
              <li>• Pantalla LED de avisos.</li>
              <li>• Teclado metálico alfanumérico para placa y programación.</li>
              <li>• 2 impresoras integradas por equipo.</li>
            </ul>

            <button
              ref="buttonRef"
              @mousemove="handleMagnet"
              @mouseleave="resetMagnet"
              class="bg-white text-black font-black uppercase px-8 py-4 rounded-xl transition-all duration-300 hover:bg-blue-500 hover:text-white"
            >
              Solicitar ficha técnica
            </button>

          </div>

        </article>

        <!-- SECUNDARIOS -->
        <div class="flex flex-col gap-8 md:col-span-4">

          <article
            v-for="(product, index) in products.slice(1)"
            :key="index"
            class="group relative flex-1 rounded-2xl bg-gradient-to-br from-[#0c111c] to-[#050810] border border-white/10 transition-all duration-1000 ease-out overflow-hidden"
            :class="hasAnimated ? 'opacity-100 translate-y-0' : 'opacity-95 translate-y-8'"
            :style="{ transitionDelay: `${index * 150}ms` }"
          >

            <div class="h-52 md:h-60 flex items-center justify-center p-6">
              <img
                :src="product.imageUrl"
                :alt="product.name"
                class="max-h-full max-w-full object-contain transition-transform duration-700 group-hover:scale-105"
                loading="lazy"
              />
            </div>

            <div class="px-6 pb-6">
              <h4 class="text-xl font-black uppercase text-white">
                {{ product.name }}
              </h4>

              <p class="text-xs uppercase tracking-widest text-blue-500 mt-2">
                {{ product.brand }}
              </p>
            </div>

          </article>

        </div>

      </div>
    </div>
  </section>
</template>
