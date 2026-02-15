<template>  
  <section
    ref="sectionRef"
    aria-label="Nuestros Servicios"
    class="relative w-full h-screen overflow-hidden flex items-center justify-center bg-gradient-to-b from-gray-950 via-black to-gray-900 text-white"
  >

    <!-- TÍTULO SEO -->
    <header class="absolute top-8 w-full text-center z-40 pointer-events-none px-4">
      <h2 class="font-black leading-none tracking-tight text-[clamp(40px,6vw,90px)]">
        NUESTROS 
        <span class="italic text-blue-500">SERVICIOS.</span>
      </h2>
    </header>

    <div class="absolute inset-0 bg-[radial-gradient(circle_at_center,rgba(255,255,255,0.08),transparent_60%)]"></div>

    <!-- Flechas -->
    <button 
      aria-label="Servicio anterior"
      class="absolute left-6 md:left-10 top-1/2 -translate-y-1/2 w-12 h-12 md:w-14 md:h-14 rounded-full border border-white/30 backdrop-blur-xl bg-white/10 text-white text-2xl md:text-3xl z-30 transition-all duration-300 hover:scale-110 hover:bg-white/20"
      @click="prevCard"
    >
      ‹
    </button>

    <button 
      aria-label="Siguiente servicio"
      class="absolute right-6 md:right-10 top-1/2 -translate-y-1/2 w-12 h-12 md:w-14 md:h-14 rounded-full border border-white/30 backdrop-blur-xl bg-white/10 text-white text-2xl md:text-3xl z-30 transition-all duration-300 hover:scale-110 hover:bg-white/20"
      @click="nextCard"
    >
      ›
    </button>

    <!-- CÁMARA -->
    <div
      class="w-full h-full perspective-[2000px] transform-style-preserve-3d cursor-grab"
      :style="cameraStyle"
      @mousedown="startDrag"
      @mousemove="onDrag"
      @mouseup="endDrag"
      @mouseleave="endDrag"
      @touchstart="startTouch"
      @touchmove="onTouch"
      @touchend="endDrag"
    >
      <div class="relative w-full h-full transform-style-preserve-3d">
        <article
          v-for="(service, i) in services"
          :key="i"
          class="absolute left-1/2 top-1/2 rounded-2xl overflow-hidden backdrop-blur-2xl bg-white/5 border border-white/20 shadow-[0_40px_120px_rgba(0,0,0,0.6)] group"
          :style="getCardStyle(i)"
        >

          <img
            :src="service.image"
            :alt="service.title"
            class="w-full h-full object-cover"
            loading="lazy"
          />

          <!-- Overlay -->
          <div class="absolute bottom-0 w-full p-5 bg-gradient-to-t from-black/90 to-transparent">
            
            <!-- TÍTULO con línea animada Tailwind -->
            <h3
              class="relative inline-block font-semibold text-lg md:text-xl leading-snug tracking-tight after:content-[''] after:absolute after:left-0 after:-bottom-2 after:h-[2px] after:w-2/3 after:bg-gradient-to-r after:from-blue-500 after:to-transparent after:transition-all after:duration-500 group-hover:after:w-full"
            >
              {{ service.title }}
            </h3>

            <p class="mt-4 text-sm md:text-base text-gray-200 leading-relaxed">
              {{ service.description }}
            </p>

          </div>

          <!-- Reflejo -->
          <div class="absolute bottom-[-100%] w-full h-full scale-y-[-1] opacity-25 [mask-image:linear-gradient(to_bottom,rgba(0,0,0,0.4),transparent)]">
            <img :src="service.image" class="w-full h-full object-cover" />
          </div>

          <!-- Sombra -->
          <div class="absolute -bottom-10 w-3/5 h-10 left-1/5 bg-[radial-gradient(ellipse_at_center,rgba(0,0,0,0.6),transparent)] blur-xl rotate-x-90"></div>

        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from "vue"
import { gsap } from "gsap"
import canopy from '@/assets/images/mantenimiento_canopy.webp'
import surtidores from '@/assets/images/surtidores.webp'
import hidraulicas from '@/assets/images/hidraulicas.webp'
import confinados from '@/assets/images/confinados.webp'
import lavado_tanques from '@/assets/images/aspirada_tanques.webp'
import mantenimiento_bombas from '@/assets/images/mantenimiento_bombas.webp'
import prueba_hidrostatica from '@/assets/images/prueba_hidrostatica.webp'
import instalacion_mantenimiento_electrico from '@/assets/images/instalacion_mantenimiento_electrico.webp'
import mantenimiento_precios from '@/assets/images/mantenimiento_precios.webp'
import obras_civiles from '@/assets/images/obras_civiles.webp'

const cardWidth = ref(260)
const cardHeight = ref(360)
const radius = ref(380)

const sectionRef = ref(null)

const services = ref([
  { title: "Servicio Técnico", description: "Mantenimiento Canopy.", image: canopy },
  { title: "Servicio Técnico", description: "Mantenimiento Surtidores.", image: surtidores },
  { title: "Servicio Técnico", description: "Adecuaciones Hidráulicas.", image: hidraulicas },
  { title: "Servicio Técnico", description: "Lavado con ingreso a tanques de combustible, contamos con certificado de espacios confinados.", image: confinados },
  { title: "Servicio", description: "Aspirado de tanques de combustible.", image: lavado_tanques },
  { title: "Servicio", description: "Mantenimiento a bombas sumergibles", image: mantenimiento_bombas },
  { title: "Servicio", description: "Prueba hidrostática de tanques", image: prueba_hidrostatica },
  { title: "Servicio", description: "Instalación y revisión eléctrica", image: instalacion_mantenimiento_electrico },
  { title: "Servicio", description: "Mantenimiento a avisasos de precios", image: mantenimiento_precios },
  { title: "Servicio", description: "Obras civiles", image: obras_civiles },
])

const rotation = ref(0)
const velocity = ref(0)
const mouseX = ref(0)
const isDragging = ref(false)
const isAnimating = ref(false)

let lastX = 0
let observer

const angleStep = computed(() => 360 / services.value.length)

onMounted(() => {
  observer = new IntersectionObserver(entries => {
    if (entries[0].isIntersecting && !isDragging.value && !isAnimating.value) {
      velocity.value += 0.002
    }
  }, { threshold: 0.6 })

  observer.observe(sectionRef.value)
  window.addEventListener("wheel", onScroll)
  window.addEventListener("mousemove", onMouseMove)
  gsap.ticker.add(animate)
})

onUnmounted(() => {
  observer.disconnect()
  gsap.ticker.remove(animate)
})

function startDrag(e) {
  isDragging.value = true
  lastX = e.clientX
}

function onDrag(e) {
  if (!isDragging.value) return
  const delta = e.clientX - lastX
  velocity.value = delta * 0.002
  lastX = e.clientX
}

function startTouch(e) {
  isDragging.value = true
  lastX = e.touches[0].clientX
}

function onTouch(e) {
  const delta = e.touches[0].clientX - lastX
  velocity.value = delta * 0.002
  lastX = e.touches[0].clientX
}

function endDrag() {
  isDragging.value = false
}

function onScroll(e) {
  velocity.value += e.deltaY * 0.0003
}

function onMouseMove(e) {
  mouseX.value = (e.clientX / window.innerWidth - 0.5) * 2
}

function animate() {
  velocity.value *= 0.95
  rotation.value += velocity.value * 60
}

function getCurrentIndex() {
  const normalized = ((rotation.value % 360) + 360) % 360
  return Math.round(normalized / angleStep.value) % services.value.length
}

function goToIndex(index) {
  if (isAnimating.value) return
  isAnimating.value = true

  const targetAngle = index * angleStep.value

  gsap.to(rotation, {
    value: targetAngle,
    duration: 1,
    ease: "power3.out",
    onComplete: () => isAnimating.value = false
  })
}

function nextCard() {
  const current = getCurrentIndex()
  goToIndex((current + 1) % services.value.length)
}

function prevCard() {
  const current = getCurrentIndex()
  goToIndex((current - 1 + services.value.length) % services.value.length)
}

function getCardStyle(i) {
  const angle = angleStep.value * i + rotation.value
  const rad = (angle * Math.PI) / 180

  const x = Math.sin(rad) * radius.value
  const z = Math.cos(rad) * radius.value

  const scale = 0.7 + (z / radius.value) * 0.5
  const fog = 1 - Math.max(0, (radius.value - z) / (radius.value * 2))
  const blur = Math.abs(velocity.value) * 20

  return {
    width: `${cardWidth.value}px`,
    height: `${cardHeight.value}px`,
    marginLeft: `-${cardWidth.value / 2}px`,
    marginTop: `-${cardHeight.value / 2}px`,
    transform: `translateX(${x}px) translateZ(${z}px) scale(${scale})`,
    filter: `brightness(${0.6 + (z / radius.value) * 0.6}) blur(${blur}px)`,
    opacity: fog,
    zIndex: Math.floor(z)
  }
}

const cameraStyle = computed(() => ({
  transform: `rotateY(${mouseX.value * 12}deg)`
}))
</script>
