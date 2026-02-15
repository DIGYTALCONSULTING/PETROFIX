<script setup>
import poster from '@/assets/images/bg_hero_petrofix.webp'
</script>

<template>
  <section
    id="inicio"
    aria-label="Hero Petrofix"
    class="relative min-h-screen flex items-center justify-center overflow-hidden"
  >
    <!-- VIDEO BACKGROUND -->
    <div class="absolute inset-0 z-0">
      <video
        autoplay
        muted
        loop
        playsinline
        :poster="poster"
        class="h-full w-full object-cover scale-105"
      >
        <source :src="videoSrc" type="video/mp4" />
      </video>

      <div class="absolute inset-0 bg-black/60"></div>
    </div>

    <!-- CONTENT -->
    <div class="relative z-10 mx-auto max-w-7xl px-4 text-center">
      <div class="flex flex-col items-center">

        <!-- Badge -->
        <div
          class="mb-8 inline-flex items-center gap-3 rounded-full
                 border border-white bg-orange-500/10
                 px-6 py-2 text-[10px] font-black tracking-[0.3em]
                 uppercase text-orange-400"
        >
          <span class="h-2 w-2 animate-pulse rounded-full bg-orange-500"></span>
          Ingeniería para el sector petrolero
        </div>

        <!-- H1 -->
        <h1
          class="mb-8 max-w-5xl text-4xl sm:text-6xl lg:text-[8rem]
                 font-black leading-[0.9] tracking-tight text-white"
        >
          PETROFIX <br />
          <span
            class="bg-gradient-to-b from-blue-300 to-blue-700
                   bg-clip-text text-transparent italic"
          >
            SOLUCIONES INTEGRALES
          </span>
        </h1>

        <!-- Description -->
        <p
          class="mb-12 max-w-2xl text-base sm:text-xl
                 text-slate-300 leading-relaxed"
        >
          Distribuidores exclusivos en Colombia de dispensadores y surtidores marca Bluesky Energy y Technology. 
        </p>

        <!-- CTA -->
        <div class="flex flex-col gap-6 sm:flex-row sm:items-center">

          <!-- BOTON PREMIUM -->
          <a
            href="#contacto"
            class="flex items-center gap-4 rounded-2xl
                   bg-orange-600 px-10 py-5
                   text-sm sm:text-base font-black uppercase
                   tracking-widest text-white
                   hover:bg-orange-700 hover:scale-105
                   transition active:scale-95

                   animate-bounce
                   [animation-duration:2.8s]
                   [animation-timing-function:cubic-bezier(.4,0,.2,1)]
                   will-change-transform"
          >
            CONTACTANOS
            
            <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
              <path d="M13 2L3 14h7l-1 8 10-12h-7z"/>
            </svg>
          </a>

          <!-- Secondary -->
          <button
            class="group flex items-center gap-5 text-white/70 hover:text-white transition"
            aria-label="Ver operación técnica"
          >
            <div
              class="flex h-14 w-14 items-center justify-center rounded-full
                     border border-white/20
                     group-hover:bg-white group-hover:text-black
                     transition"
            >
              <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor">
                <path d="M8 5v14l11-7z"/>
              </svg>
            </div>
            <span class="text-xs font-black tracking-[0.2em] uppercase">
              Mira como lo hacemos
            </span>
          </button>
        </div>
      </div>
    </div>

    <!-- SCROLL -->
    
  </section>
</template>
