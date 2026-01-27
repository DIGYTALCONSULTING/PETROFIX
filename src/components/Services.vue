<script setup>
/*
  Servicios inline
  Sin dependencias externas
*/
const services = [
  {
    title: 'Mantenimiento de canopy',
    description:
      'Diagnóstico especializado para detección temprana de fugas y fallas estructurales en sistemas de combustible.',
    icon: 'shield',
  },
  {
    title: 'Mantenimiento de surtidores',
    description:
      'Cumplimiento total bajo resolución vigente para evitar sanciones, cierres y riesgos legales.',
    icon: 'check',
  },
  {
    title: 'Adecuaciones hidráulicas (Tuberías de combustibles)',
    description:
      'Estrategias de mantenimiento predictivo que prolongan la vida útil de su infraestructura.',
    icon: 'settings',
  },
  {
    title: 'Lavado con ingreso a tanques de combustible ',
    description:
      'Contamos con certificado de espacios confinados',
    icon: 'settings',
  },
  {
    title: 'Aspirada de tanques de combustibles.',
    description:
      'Con personal certificado y equipos de última generación',
    icon: 'settings',
  },
  {
    title: 'Mantenimiento a bombas sumergibles ',
    description:
      'Con validación de funcionamiento posterior al mantenimiento',
    icon: 'settings',
  },
  {
    title: 'Prueba hidrostática de tanques ',
    description:
      'Usamos equipos certificados para garantizar la integridad de sus tanques',
    icon: 'settings',
  },
  {
    title: 'Instalación y revisión eléctrica ',
    description:
      'Personal calificado para trabajos eléctricos en estaciones de servicio',
    icon: 'settings',
  },
  {
    title: 'Mantenimiento a avisos de precios',
    description:
      'Deja que los expertos se encarguen del mantenimiento de tus avisos de precios',
    icon: 'settings',
  },
  {
    title: 'Obras civiles',
    description:
      'Diferentes tipos de obras civiles para estaciones de servicio',
    icon: 'settings',
  },
]
</script>

<template>
  <section
    id="servicios"
    aria-label="Servicios Petrofix"
    class="relative overflow-hidden bg-[#050810] py-20 sm:py-28 lg:py-32"
  >
    <!-- Glow decorativo -->
    <div
      class="pointer-events-none absolute -top-24 right-0
             h-96 w-96 rounded-full
             bg-orange-500/10 blur-[120px]"
    ></div>

    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-12">
      <!-- Header -->
      <div
        class="mb-16 sm:mb-20
               flex flex-col gap-8
               md:flex-row md:items-end md:justify-between"
      >
        <h2
          class="max-w-3xl
                 text-4xl sm:text-6xl lg:text-7xl
                 font-black tracking-tighter
                 text-white leading-[0.95]"
        >
          INGENIERÍA <br />
          <span class="italic text-orange-500">
            CERTIFICADA
          </span>.
        </h2>
      </div>

      <!-- Grid -->
      <div class="grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
        <div
          v-for="(service, index) in services"
          :key="index"
          class="group relative overflow-hidden
                 rounded-[2.5rem]
                 border border-white/5
                 bg-white/5
                 p-8 sm:p-10
                 transition-all duration-500
                 hover:-translate-y-2
                 hover:border-orange-500/40"
        >
          <!-- Glow hover -->
          <div
            class="absolute inset-0 opacity-0
                   bg-gradient-to-br from-orange-500/10 to-transparent
                   transition group-hover:opacity-100"
          ></div>

          <!-- Icono -->
          <div
            class="relative z-10 mb-8
                   flex h-16 w-16 items-center justify-center
                   rounded-2xl
                   bg-black text-orange-500
                   transition-all duration-500
                   group-hover:bg-orange-500
                   group-hover:text-white
                   group-hover:scale-110"
          >
            <!-- SVG según tipo -->
            <svg
              v-if="service.icon === 'shield'"
              width="28"
              height="28"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
            >
              <path stroke-width="2" d="M12 2l7 4v6c0 5-3.5 9.5-7 10-3.5-.5-7-5-7-10V6l7-4z"/>
            </svg>

            <svg
              v-else-if="service.icon === 'check'"
              width="28"
              height="28"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
            >
              <path stroke-width="2" d="M5 13l4 4L19 7"/>
            </svg>

            <svg
              v-else
              width="28"
              height="28"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
            >
              <circle cx="12" cy="12" r="3" stroke-width="2"/>
              <path stroke-width="2" d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 1 1-2.83 2.83l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 1 1-4 0v-.09a1.65 1.65 0 0 0-1-1.51 1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 1 1-2.83-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 1 1 0-4h.09a1.65 1.65 0 0 0 1.51-1 1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 1 1 2.83-2.83l.06.06a1.65 1.65 0 0 0 1.82.33h.01a1.65 1.65 0 0 0 1-1.51V3a2 2 0 1 1 4 0v.09a1.65 1.65 0 0 0 1 1.51h.01a1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 1 1 2.83 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82v.01a1.65 1.65 0 0 0 1.51 1H21a2 2 0 1 1 0 4h-.09a1.65 1.65 0 0 0-1.51 1z"/>
            </svg>
          </div>

          <!-- Texto -->
          <div class="relative z-10">
            <h4
              class="mb-4 text-xl sm:text-2xl
                     font-black uppercase tracking-tight
                     text-white"
            >
              {{ service.title }}
            </h4>

            <p
              class="text-sm sm:text-base
                     font-medium leading-relaxed
                     text-slate-500"
            >
              {{ service.description }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
