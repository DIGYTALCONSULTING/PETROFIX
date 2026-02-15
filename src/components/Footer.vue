<!-- src/components/Footer.vue -->
<template>
  <footer class="bg-[#050810] pt-16 md:pt-32 pb-12 md:pb-16 border-t border-white/5">
    <div class="container mx-auto px-4 sm:px-6">
      <!-- Grid principal responsive -->
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8 sm:gap-12 md:gap-16 mb-12 md:mb-24">
        
        <!-- Columna 1: Logo y redes -->
        <div class="sm:col-span-2 lg:col-span-1">
          <div class="flex items-center gap-3 mb-6 md:mb-8">
            <!-- Logo SVG inline -->
             <img :src="logo" alt="Petrofix" class="
              h-11 sm:h-12 lg:h-14
              w-auto
              drop-shadow-[0_0_2px_#ffffff]
              transition-all duration-300 hover:drop-shadow-[0_0_6px_#ffffff]
            " />
            
            <span class="font-black text-xl md:text-2xl tracking-tight text-white uppercase">
              PETRO<span class="text-[#FF5F00]">FIX</span>
            </span>
          </div>
          
          <p class="text-gray-500 mb-6 md:mb-10 text-base md:text-lg font-medium leading-relaxed">
            Ingeniería de vanguardia para el sector Oil & Gas en Colombia.
          </p>
          
          <!-- Redes sociales -->
          <div class="flex gap-3 md:gap-4">
            <a 
              v-for="(icon, index) in socialIcons" 
              :key="index"
              href="#" 
              class="w-10 h-10 md:w-12 md:h-12 bg-[#0F1428] border border-white/5 text-gray-500 rounded-xl md:rounded-2xl flex items-center justify-center hover:bg-[#FF5F00] hover:text-white transition-all duration-300 active:scale-95"
              :aria-label="icon.label"
            >
              <component :is="icon.component" class="w-4 h-4 md:w-5 md:h-5" />
            </a>
          </div>
        </div>

        <!-- Columna 2: Explorar -->
        <div>
          <h4 class="font-black text-white text-xs md:text-sm uppercase tracking-wider md:tracking-widest mb-6 md:mb-10">
            Explorar
          </h4>
          <ul class="space-y-4 md:space-y-6 text-gray-500 font-bold text-base md:text-lg">
            <li v-for="link in exploreLinks" :key="link">
              <a 
                :href="`#${link.toLowerCase()}`" 
                class="hover:text-[#0062ff] transition-colors duration-300 block py-1 md:py-0"
              >
                {{ link }}
              </a>
            </li>
          </ul>
        </div>

        <!-- Columna 3: Recursos -->
        <div>
          <h4 class="font-black text-white text-xs md:text-sm uppercase tracking-wider md:tracking-widest mb-6 md:mb-10">
            Recursos
          </h4>
          <ul class="space-y-4 md:space-y-6 text-gray-500 font-bold text-base md:text-lg">
            <li v-for="resource in resources" :key="resource">
              <a 
                href="#" 
                class="hover:text-[#0062ff] transition-colors duration-300 block py-1 md:py-0"
              >
                {{ resource }}
              </a>
            </li>
          </ul>
        </div>

        <!-- Columna 4: Newsletter -->
        <div class="sm:col-span-2 lg:col-span-1">
          <h4 class="font-black text-white text-xs md:text-sm uppercase tracking-wider md:tracking-widest mb-6 md:mb-10">
            Newsletter
          </h4>
          <p class="text-gray-500 mb-4 md:mb-6 font-medium text-sm md:text-base">
            Reciba alertas sobre normatividad técnica.
          </p>
          
          <!-- Formulario newsletter -->
          <div class="flex flex-col sm:flex-row gap-2 md:gap-0 p-1 md:p-2 bg-[#0F1428] rounded-xl md:rounded-2xl border border-white/5">
            <input 
              type="email" 
              placeholder="Su email" 
              class="bg-transparent border-none rounded-lg px-4 py-3 md:py-2 text-white w-full outline-none text-sm md:text-base placeholder:text-gray-600"
              aria-label="Email para newsletter"
            />
            <button 
              class="bg-[#0062ff] text-white px-4 md:px-6 py-3 md:py-3 rounded-lg md:rounded-xl font-black text-xs md:text-sm hover:scale-[1.05] active:scale-95 transition-transform duration-200 whitespace-nowrap"
              type="button"
            >
              GO
            </button>
          </div>
        </div>
      </div>

      <!-- Línea divisoria y copyright -->
      <div class="flex flex-col md:flex-row items-center justify-between pt-8 md:pt-12 border-t border-white/5 gap-6 md:gap-8">
        <!-- Copyright -->
        <p class="text-gray-600 text-xs font-bold uppercase tracking-wider text-center md:text-left">
          © {{ currentYear }} PETROFIX S.A.S. • ELITE SOLUTIONS
        </p>
        
        <!-- Botón scroll to top -->
        <button 
          @click="scrollToTop"
          class="flex items-center gap-2 md:gap-3 text-gray-600 hover:text-[#FF5F00] font-black uppercase tracking-wider text-xs group transition-all duration-300"
          aria-label="Volver al inicio"
        >
          VOLVER AL INICIO
          <svg 
            class="w-5 h-5 md:w-6 md:h-6 group-hover:-translate-y-1 md:group-hover:-translate-y-2 transition-transform duration-300" 
            fill="none" 
            stroke="currentColor" 
            viewBox="0 0 24 24"
          >
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 11l3-3m0 0l3 3m-3-3v8m0-13a9 9 0 110 18 9 9 0 010-18z" />
          </svg>
        </button>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { computed, defineComponent, h } from 'vue'
import logo from '@/assets/images/logo_PT.png'
// Año actual
const currentYear = computed(() => new Date().getFullYear())

// Función scroll suave al inicio
const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  })
}

// Links de exploración
const exploreLinks = ['Servicios', 'Equipos', 'Certificaciones', 'Contacto']

// Recursos
const resources = ['Ayuda Técnica', 'Soporte 24/7', 'Aviso Legal', 'Políticas']

// Componentes SVG para redes sociales
const InstagramIcon = defineComponent({
  render() {
    return h('svg', {
      class: 'w-4 h-4 md:w-5 md:h-5',
      fill: 'none',
      stroke: 'currentColor',
      viewBox: '0 0 24 24'
    }, [
      h('path', {
        strokeLinecap: 'round',
        strokeLinejoin: 'round',
        strokeWidth: 2,
        d: 'M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z'
      }),
      h('path', {
        strokeLinecap: 'round',
        strokeLinejoin: 'round',
        strokeWidth: 2,
        d: 'M15 11a3 3 0 11-6 0 3 3 0 016 0z'
      })
    ])
  }
})

const FacebookIcon = defineComponent({
  render() {
    return h('svg', {
      class: 'w-4 h-4 md:w-5 md:h-5',
      fill: 'none',
      stroke: 'currentColor',
      viewBox: '0 0 24 24'
    }, [
      h('path', {
        strokeLinecap: 'round',
        strokeLinejoin: 'round',
        strokeWidth: 2,
        d: 'M18 2h-3a5 5 0 00-5 5v3H7v4h3v8h4v-8h3l1-4h-4V7a1 1 0 011-1h3z'
      })
    ])
  }
})

const LinkedinIcon = defineComponent({
  render() {
    return h('svg', {
      class: 'w-4 h-4 md:w-5 md:h-5',
      fill: 'none',
      stroke: 'currentColor',
      viewBox: '0 0 24 24'
    }, [
      h('path', {
        strokeLinecap: 'round',
        strokeLinejoin: 'round',
        strokeWidth: 2,
        d: 'M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z'
      })
    ])
  }
})

// Array de redes sociales
const socialIcons = [
  { component: InstagramIcon, label: 'Instagram' },
  { component: FacebookIcon, label: 'Facebook' },
  { component: LinkedinIcon, label: 'LinkedIn' }
]
</script>

<style scoped>
/* Animación sutil para botones */
button {
  transform: translateZ(0);
  backface-visibility: hidden;
}

/* Mejora en la legibilidad en móviles */
@media (max-width: 640px) {
  a {
    padding: 0.25rem 0;
  }
}

/* Transición suave para hover */
* {
  transition-property: color, background-color, border-color, transform, opacity;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  transition-duration: 200ms;
}

</style>