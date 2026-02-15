<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

/* MÉTRICAS EDITABLES */
const metrics = [
  { value: 20, suffix: '+', label: 'Proyectos Activos' },
  { value: 8, suffix: '+', label: 'Aliados Estratégicos' },
  { value: 100, suffix: '%', label: 'Efectividad Técnica' },
]

/* estado animado */
const counts = ref(metrics.map(() => 0))
let observer = null

/* animación conteo */
const animateCount = (index, target) => {
  let start = 0
  const duration = 1800 // velocidad elegante
  const startTime = performance.now()

  const update = (currentTime) => {
    const elapsed = currentTime - startTime
    const progress = Math.min(elapsed / duration, 1)

    // easing suave premium
    const easeOut = 1 - Math.pow(1 - progress, 3)

    counts.value[index] = Math.floor(easeOut * target)

    if (progress < 1) {
      requestAnimationFrame(update)
    } else {
      counts.value[index] = target
    }
  }

  requestAnimationFrame(update)
}

/* cuando entra en pantalla */
onMounted(() => {
  const section = document.querySelector('#metrics-section')

  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          metrics.forEach((m, i) => {
            counts.value[i] = 0
            animateCount(i, m.value)
          })
        }
      })
    },
    {
      threshold: 0.5, // cuando se ve 50%
    }
  )

  if (section) observer.observe(section)
})

onBeforeUnmount(() => {
  if (observer) observer.disconnect()
})
</script>

<template>
  <section
    id="metrics-section"
    aria-label="Métricas clave Petrofix"
    class="overflow-hidden border-y border-white/5 bg-[#050810] py-16 sm:py-20"
  >
    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-12">
      <div
        class="grid grid-cols-1 divide-y divide-white/5
               md:grid-cols-3 md:divide-y-0 md:divide-x"
      >
        <div
          v-for="(metric, index) in metrics"
          :key="index"
          class="group py-10 text-center transition"
        >
          <!-- VALOR animado -->
          <h3
            class="mb-3 text-5xl sm:text-6xl
                   font-black tracking-tighter
                   text-white
                   transition-colors duration-300
                   group-hover:text-blue-500"
          >
            {{ counts[index] }}{{ metric.suffix }}
          </h3>

          <!-- LABEL -->
          <p
            class="text-xs font-bold uppercase
                   tracking-[0.2em]
                   text-slate-400"
          >
            {{ metric.label }}
          </p>
        </div>
      </div>
    </div>
  </section>
</template>
