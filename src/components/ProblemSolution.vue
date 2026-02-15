<script setup>
import { ref, onMounted, onUnmounted } from "vue"

const sectionRef = ref(null)
const cardRef = ref(null)
const isVisible = ref(false)

let observer
let animationFrame
let particles = []

/* ===============================
   REVEAL AL ENTRAR EN VIEWPORT
================================= */
onMounted(() => {
  observer = new IntersectionObserver(
    ([entry]) => {
      isVisible.value = entry.isIntersecting
    },
    { threshold: 0.3 }
  )

  observer.observe(sectionRef.value)

  createParticles()
  animateParticles()
})

onUnmounted(() => {
  observer.disconnect()
  cancelAnimationFrame(animationFrame)
})

/* ===============================
   PARALLAX + ILUMINACIÓN
================================= */
function handleMouseMove(e) {
  const rect = cardRef.value.getBoundingClientRect()
  const x = (e.clientX - rect.left) / rect.width - 0.5
  const y = (e.clientY - rect.top) / rect.height - 0.5

  cardRef.value.style.transform = `
    rotateX(${y * 6}deg)
    rotateY(${x * 6}deg)
  `

  cardRef.value.style.setProperty("--mouse-x", `${e.clientX - rect.left}px`)
  cardRef.value.style.setProperty("--mouse-y", `${e.clientY - rect.top}px`)
}

function resetCard() {
  cardRef.value.style.transform = `rotateX(0deg) rotateY(0deg)`
}

/* ===============================
   PARTÍCULAS INDUSTRIALES
================================= */
function createParticles() {
  const container = document.getElementById("particles")

  for (let i = 0; i < 30; i++) {
    const el = document.createElement("div")
    el.className =
      "absolute w-[2px] h-[2px] bg-white/20 rounded-full blur-[1px]"
    container.appendChild(el)

    particles.push({
      el,
      x: Math.random() * window.innerWidth,
      y: Math.random() * window.innerHeight,
      speed: Math.random() * 0.4 + 0.1
    })
  }
}

function animateParticles() {
  particles.forEach(p => {
    p.y -= p.speed
    if (p.y < 0) p.y = window.innerHeight
    p.el.style.transform = `translate(${p.x}px, ${p.y}px)`
  })

  animationFrame = requestAnimationFrame(animateParticles)
}
</script>

<template>
  <section
    ref="sectionRef"
    id="problema"
    aria-label="Problema y solución Petrofix"
    class="relative overflow-hidden bg-[#050810] py-20 sm:py-28 lg:py-32 text-white"
  >
    <!-- Partículas -->
    <div id="particles" class="absolute inset-0 pointer-events-none z-0"></div>

    <!-- Glow -->
    <div class="absolute top-1/4 -left-24 h-96 w-96 rounded-full bg-orange-500/10 blur-[140px]" />
    <div class="absolute bottom-0 right-0 h-[500px] w-[500px] rounded-full bg-blue-500/10 blur-[180px]" />

    <!-- Blueprint -->
    <div class="absolute inset-0 opacity-[0.04] pointer-events-none"
         style="background-image: linear-gradient(to right, white 1px, transparent 1px),
                                 linear-gradient(to bottom, white 1px, transparent 1px);
                background-size: 80px 80px;
                animation: blueprintMove 20s linear infinite;">
    </div>

    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-12 relative z-10">
      <div class="grid gap-16 lg:grid-cols-2 lg:gap-20 items-center">

        <!-- TEXTO COMPLETO ORIGINAL -->
        <div :class="isVisible ? 'opacity-100 translate-y-0 transition-all duration-1000' : 'opacity-0 translate-y-10'">

          <h2 class="mb-10 text-4xl sm:text-6xl lg:text-7xl font-black leading-[0.95] tracking-tighter">
            EL RIESGO <br />
            ES <span class="italic text-blue-500">INVISIBLE</span>.
          </h2>

          <p class="mb-12 max-w-xl text-base sm:text-lg lg:text-xl font-medium leading-relaxed text-slate-400">
            Una pequeña fisura en su sistema de combustible no solo es
            una pérdida económica; es una amenaza legal y ambiental inmediata.
            En PETROFIX eliminamos la incertidumbre con tecnología.
          </p>

          <!-- BLOQUES RESTAURADOS -->
          <div class="space-y-6">

            <!-- Item 1 -->
            <div
              class="group flex gap-6 rounded-3xl border border-white/5 bg-white/5 p-6 sm:p-8 backdrop-blur-xl transition duration-500 hover:translate-x-3 hover:border-orange-500/40 hover:bg-white/10"
            >
              <div class="shrink-0 text-blue-500 transition group-hover:scale-110">
                <svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                  <path stroke-width="2" d="M12 9v4m0 4h.01M5 20h14l-7-16-7 16z"/>
                </svg>
              </div>

              <div>
                <h4 class="mb-2 text-lg sm:text-xl font-black uppercase text-white">
                  Sanciones Normativas
                </h4>
                <p class="text-sm sm:text-base text-slate-400 font-medium leading-relaxed">
                  Sin monitoreo profesional, su EDS está expuesta a cierres
                  y multas millonarias por incumplimiento.
                </p>
              </div>
            </div>

            <!-- Item 2 -->
            <div
              class="group flex gap-6 rounded-3xl border border-white/5 bg-white/5 p-6 sm:p-8 backdrop-blur-xl transition duration-500 hover:translate-x-3 hover:border-orange-500/40 hover:bg-white/10"
            >
              <div class="shrink-0 text-blue-500 transition group-hover:scale-110">
                <svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                  <circle cx="12" cy="12" r="10" stroke-width="2"/>
                  <path stroke-width="2" d="M12 6v6l4 2"/>
                </svg>
              </div>

              <div>
                <h4 class="mb-2 text-lg sm:text-xl font-black uppercase text-white">
                  Fugas no Detectadas
                </h4>
                <p class="text-sm sm:text-base text-slate-400 font-medium leading-relaxed">
                  El desgaste microscópico puede reducir la eficiencia
                  operativa de su inventario hasta en un 40% anual.
                </p>
              </div>
            </div>

          </div>
        </div>

        <!-- TARJETA SOLUCIÓN COMPLETA -->
        <div
          ref="cardRef"
          @mousemove="handleMouseMove"
          @mouseleave="resetCard"
          class="relative rounded-[3.5rem] p-[2px] transition-all duration-1000"
          :class="isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'"
        >
          <!-- Energía borde -->
          <div class="absolute inset-0 rounded-[3.5rem] border border-blue-500/30 animate-borderGlow pointer-events-none"></div>

          <div
            class="relative flex min-h-[460px] flex-col justify-between overflow-hidden rounded-[3.4rem] bg-[#050810] p-8 sm:p-12 shadow-[0_40px_120px_-20px_rgba(0,0,0,0.6)]"
            style="
              background:
              radial-gradient(circle at var(--mouse-x,50%) var(--mouse-y,50%),
              rgba(59,130,246,0.15),
              rgba(5,8,16,1) 60%),
              repeating-linear-gradient(
                45deg,
                rgba(255,255,255,0.02) 0px,
                rgba(255,255,255,0.02) 2px,
                transparent 2px,
                transparent 6px
              );
            "
          >
            <!-- Imagen fondo -->
            <img
              src="https://images.unsplash.com/photo-1542332213-9b5a5a3fad35?q=80&w=800&auto=format&fit=crop"
              alt="Infraestructura industrial"
              class="absolute inset-0 h-full w-full object-cover opacity-10"
            />

            <div class="relative z-10">
              <h3 class="mb-6 text-3xl sm:text-4xl font-black uppercase text-white">
                Nuestro Blindaje
              </h3>

              <p class="mb-10 text-lg sm:text-xl font-medium italic leading-relaxed text-slate-400">
                “Transformamos vulnerabilidades críticas en fortalezas
                operativas bajo estándares internacionales.”
              </p>

              <ul class="space-y-6">
                <li class="flex items-center gap-4 text-lg font-black text-white">
                  <span class="h-3 w-3 rounded-full bg-blue-500 animate-pulse"></span>
                  SERVICIOS TÉCNICOS
                </li>
                <li class="flex items-center gap-4 text-lg font-black text-white">
                  <span class="h-3 w-3 rounded-full bg-blue-500 animate-pulse"></span>
                  SURTIDORES Y DISPENSADORES
                </li>
                <li class="flex items-center gap-4 text-lg font-black text-white">
                  <span class="h-3 w-3 rounded-full bg-blue-500 animate-pulse"></span>
                  ACCESORIOS
                </li>
              </ul>
            </div>

            <div class="relative z-10 mt-10">
              <button
                class="w-full rounded-2xl bg-white py-5 sm:py-6 text-base sm:text-xl font-black uppercase text-black transition-all duration-500 hover:scale-[1.02] hover:bg-blue-500 hover:text-white"
              >
                Programe su Revisión aquí
              </button>
            </div>

          </div>
        </div>

      </div>
    </div>
  </section>
</template>

<style scoped>
@keyframes blueprintMove {
  from { background-position: 0 0; }
  to { background-position: 80px 80px; }
}

@keyframes borderGlow {
  0% { box-shadow: 0 0 0px rgba(59,130,246,0.2); }
  50% { box-shadow: 0 0 30px rgba(59,130,246,0.6); }
  100% { box-shadow: 0 0 0px rgba(59,130,246,0.2); }
}

.animate-borderGlow {
  animation: borderGlow 4s ease-in-out infinite;
}
</style>
