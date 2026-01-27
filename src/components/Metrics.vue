<script setup>
/**
 * MÉTRICAS
 * Todo inline, sin dependencias externas
 * Escalable y fácil de editar
 */
const metrics = [
  { value: '+20', label: 'Proyectos Activos' },
  { value: '+8', label: 'Aliados Estratégicos' },
  { value: '100%', label: 'Efectividad Técnica' },
]
</script>

<template>
  <section
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
          <!-- VALOR -->
          <h3
            class="mb-3 text-5xl sm:text-6xl
                   font-black tracking-tighter
                   text-white
                   transition-colors duration-300
                   group-hover:text-orange-500"
          >
            {{ metric.value }}
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
