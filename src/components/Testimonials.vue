<script setup>
const testimonials = [
  {
    name: 'Carlos Ramírez',
    role: 'Gerente de Operaciones',
    text: 'Petrofix nos permitió detectar fallas críticas antes de que se convirtieran en sanciones costosas.',
    imageUrl: 'https://randomuser.me/api/portraits/men/32.jpg',
  },
  {
    name: 'Laura Gómez',
    role: 'Directora Técnica',
    text: 'La precisión técnica y el acompañamiento normativo marcaron la diferencia en nuestra operación.',
    imageUrl: 'https://randomuser.me/api/portraits/women/44.jpg',
  },
  {
    name: 'Andrés Muñoz',
    role: 'CEO',
    text: 'Hoy operamos con total tranquilidad gracias a la auditoría forense de Petrofix.',
    imageUrl: 'https://randomuser.me/api/portraits/men/65.jpg',
  },
]
</script>

<template>
  <section
    aria-label="Testimonios de clientes Petrofix"
    class="relative bg-[#050810] py-20 sm:py-28 lg:py-32 overflow-hidden"
  >
    <!-- Glow ambiental -->
    <div
      class="pointer-events-none absolute -bottom-40 left-1/2
             h-[500px] w-[500px] -translate-x-1/2
             rounded-full bg-orange-500/10 blur-[180px]"
    ></div>

    <div class="relative z-10 mx-auto max-w-7xl px-4 sm:px-6 lg:px-12">

      <!-- Header -->
      <div class="mb-16 sm:mb-24 text-center">
        <h2
          class="text-4xl sm:text-5xl lg:text-6xl
                 font-black uppercase tracking-tighter text-white"
        >
          Voces de
          <span class="italic text-blue-500">
            Confianza
          </span>
        </h2>

        <div class="mx-auto mt-6 h-[2px] w-24 bg-gradient-to-r from-transparent via-orange-500 to-transparent"></div>
      </div>

      <!-- Grid -->
      <div class="grid gap-8 md:grid-cols-3">
        <div
          v-for="(t, index) in testimonials"
          :key="index"
          class="group relative overflow-hidden
                 rounded-[2.5rem]
                 border border-white/10
                 bg-[#0c1220]
                 p-8 sm:p-10
                 shadow-xl
                 transition-all duration-500 ease-out
                 hover:-translate-y-3
                 hover:shadow-2xl
                 hover:border-orange-500/50"
        >
          <!-- Top Accent Line -->
          <div
            class="absolute top-0 left-0 h-[3px] w-full
                   bg-gradient-to-r from-transparent via-orange-500/70 to-transparent
                   opacity-0 transition duration-500
                   group-hover:opacity-100"
          ></div>

          <!-- Quote decorativo -->
          <div
            class="absolute right-8 top-6
                   text-[100px] leading-none
                   font-black
                   text-orange-500/5
                   pointer-events-none"
          >
            “
          </div>

          <!-- Header -->
          <div class="relative z-10 mb-8 flex items-center gap-5">
            <div
              class="h-16 w-16 overflow-hidden rounded-2xl
                     border border-orange-500/30
                     transition duration-500
                     group-hover:border-orange-500/70"
            >
              <img
                :src="t.imageUrl"
                :alt="t.name"
                class="h-full w-full object-cover
                       transition-transform duration-700
                       group-hover:scale-110"
                loading="lazy"
              />
            </div>

            <div>
              <h4 class="text-lg sm:text-xl font-bold text-white tracking-tight">
                {{ t.name }}
              </h4>

              <p
                class="text-xs font-black uppercase tracking-widest
                       text-blue-500"
              >
                {{ t.role }}
              </p>
            </div>
          </div>

          <!-- Texto -->
          <p
            class="relative z-10
                   text-base sm:text-lg
                   font-medium italic
                   leading-relaxed
                   text-slate-300"
          >
            “{{ t.text }}”
          </p>

          <!-- Hover Glow -->
          <div
            class="pointer-events-none absolute inset-0
                   opacity-0
                   bg-gradient-to-br from-orange-500/10 to-transparent
                   transition duration-700
                   group-hover:opacity-100"
          ></div>
        </div>
      </div>

    </div>
  </section>
</template>
