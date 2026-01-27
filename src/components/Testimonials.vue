<script setup>
/*
  Testimonios inline
  Sin dependencias externas
*/
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
      class="pointer-events-none absolute -bottom-32 left-1/2
             h-96 w-96 -translate-x-1/2
             rounded-full bg-orange-500/10 blur-[140px]"
    ></div>

    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-12">
      <!-- Header -->
      <div class="mb-16 sm:mb-24 text-center">
        <h2
          class="text-4xl sm:text-5xl lg:text-6xl
                 font-black uppercase tracking-tighter text-white"
        >
          Voces de
          <span class="italic text-orange-500">
            Confianza
          </span>
        </h2>
      </div>

      <!-- Grid -->
      <div class="grid gap-8 md:grid-cols-3">
        <div
          v-for="(t, index) in testimonials"
          :key="index"
          class="group relative overflow-hidden
                 rounded-[3rem]
                 border border-white/5
                 bg-white/5
                 p-8 sm:p-10
                 transition-all duration-500
                 hover:-translate-y-2
                 hover:border-orange-500/40"
        >
          <!-- Quote decorativo -->
          <div
            class="absolute right-8 top-8
                   text-7xl font-black
                   text-orange-500/10
                   transition group-hover:text-orange-500/20"
          >
            “
          </div>

          <!-- Header -->
          <div class="relative z-10 mb-8 flex items-center gap-5">
            <div
              class="h-16 w-16 overflow-hidden rounded-2xl
                     border-2 border-orange-500/20
                     transition group-hover:border-orange-500/60"
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
              <h4 class="text-lg sm:text-xl font-bold text-white">
                {{ t.name }}
              </h4>
              <p
                class="text-xs font-black uppercase tracking-widest
                       text-orange-500"
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
                   text-slate-400"
          >
            “{{ t.text }}”
          </p>

          <!-- Glow hover -->
          <div
            class="pointer-events-none absolute inset-0
                   opacity-0
                   bg-gradient-to-br from-orange-500/10 to-transparent
                   transition group-hover:opacity-100"
          ></div>
        </div>
      </div>
    </div>
  </section>
</template>
