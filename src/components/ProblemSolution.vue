<script setup>
/*
  Componente sin dependencias externas
  Vue 3 + Tailwind CSS
  Mobile-first y production-ready
*/
</script>

<template>
  <section
    id="problema"
    aria-label="Problema y solución Petrofix"
    class="relative overflow-hidden bg-[#050810] py-20 sm:py-28 lg:py-32"
  >
    <!-- Glow decorativo -->
    <div
      class="pointer-events-none absolute top-1/4 -left-24
             h-96 w-96 rounded-full
             bg-orange-500/10 blur-[120px]"
    ></div>

    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-12">
      <div class="grid gap-16 lg:grid-cols-2 lg:gap-20 items-center">

        <!-- TEXTO -->
        <div>
          <h2
            class="mb-10 text-4xl sm:text-6xl lg:text-7xl
                   font-black leading-[0.95]
                   tracking-tighter text-white"
          >
            EL RIESGO <br />
            ES
            <span class="italic text-orange-500">
              INVISIBLE
            </span>.
          </h2>

          <p
            class="mb-12 max-w-xl
                   text-base sm:text-lg lg:text-xl
                   font-medium leading-relaxed
                   text-slate-400"
          >
            Una pequeña fisura en su sistema de combustible no solo es
            una pérdida económica; es una amenaza legal y ambiental inmediata.
            En PETROFIX eliminamos la incertidumbre con tecnología.
          </p>

          <!-- BLOQUES -->
          <div class="space-y-6">
            <!-- Item -->
            <div
              class="group flex gap-6 rounded-3xl
                     border border-white/5 bg-white/5
                     p-6 sm:p-8
                     transition hover:translate-x-2
                     hover:border-orange-500/30"
            >
              <!-- Icono -->
              <div class="shrink-0 text-orange-500 transition group-hover:scale-110">
                <svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                  <path stroke-width="2" d="M12 9v4m0 4h.01M5 20h14l-7-16-7 16z"/>
                </svg>
              </div>

              <div>
                <h4 class="mb-2 text-lg sm:text-xl font-black uppercase text-white">
                  Sanciones Normativas
                </h4>
                <p class="text-sm sm:text-base text-slate-500 font-medium leading-relaxed">
                  Sin monitoreo profesional, su EDS está expuesta a cierres
                  y multas millonarias por incumplimiento.
                </p>
              </div>
            </div>

            <!-- Item -->
            <div
              class="group flex gap-6 rounded-3xl
                     border border-white/5 bg-white/5
                     p-6 sm:p-8
                     transition hover:translate-x-2
                     hover:border-orange-500/30"
            >
              <!-- Icono -->
              <div class="shrink-0 text-orange-500 transition group-hover:scale-110">
                <svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                  <circle cx="12" cy="12" r="10" stroke-width="2"/>
                  <path stroke-width="2" d="M12 6v6l4 2"/>
                </svg>
              </div>

              <div>
                <h4 class="mb-2 text-lg sm:text-xl font-black uppercase text-white">
                  Fugas no Detectadas
                </h4>
                <p class="text-sm sm:text-base text-slate-500 font-medium leading-relaxed">
                  El desgaste microscópico puede reducir la eficiencia
                  operativa de su inventario hasta en un 40% anual.
                </p>
              </div>
            </div>
          </div>
        </div>

        <!-- TARJETA SOLUCIÓN -->
        <div class="relative">
          <div
            class="rounded-[3.5rem] bg-orange-500 p-1
                   shadow-[0_30px_100px_-15px_rgba(255,95,0,0.3)]"
          >
            <div
              class="relative flex min-h-[460px] flex-col justify-between
                     overflow-hidden rounded-[3.4rem]
                     bg-[#050810] p-8 sm:p-12"
            >
              <!-- Imagen fondo -->
              <img
                src="https://images.unsplash.com/photo-1542332213-9b5a5a3fad35?q=80&w=800&auto=format&fit=crop"
                alt="Infraestructura industrial"
                class="absolute inset-0 h-full w-full object-cover
                       opacity-10 mix-blend-overlay"
              />

              <!-- Icono decorativo -->
              <div class="absolute right-8 top-8 text-orange-500/10">
                <svg width="120" height="120" viewBox="0 0 24 24" fill="currentColor">
                  <path d="M5 13l4 4L19 7"/>
                </svg>
              </div>

              <!-- Contenido -->
              <div class="relative z-10">
                <h3
                  class="mb-6 text-3xl sm:text-4xl
                         font-black uppercase tracking-tight
                         text-white"
                >
                  Nuestro Blindaje
                </h3>

                <p
                  class="mb-10 text-lg sm:text-xl
                         font-medium italic leading-relaxed
                         text-slate-400"
                >
                  “Transformamos vulnerabilidades críticas en fortalezas
                  operativas bajo estándares internacionales.”
                </p>

                <ul class="space-y-6">
                  <li class="flex items-center gap-4 text-lg font-black text-white">
                    <span class="h-3 w-3 rounded-full bg-orange-500"></span>
                    SERVICIOS TÉCNICOS
                  </li>
                  <li class="flex items-center gap-4 text-lg font-black text-white">
                    <span class="h-3 w-3 rounded-full bg-orange-500"></span>
                    SURTIDORES Y DISPENSADORES
                  </li>
                  <li class="flex items-center gap-4 text-lg font-black text-white">
                    <span class="h-3 w-3 rounded-full bg-orange-500"></span>
                    ACCESORIOS
                  </li>
                </ul>
              </div>

              <!-- CTA -->
              <div class="relative z-10 mt-10">
                <button
                  class="w-full rounded-2xl
                         bg-white py-5 sm:py-6
                         text-base sm:text-xl
                         font-black uppercase
                         text-black
                         transition
                         hover:bg-orange-500 hover:text-white"
                >
                  Progame su Revisión aquí
                </button>
              </div>
            </div>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>
