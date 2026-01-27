<!-- src/components/ContactForm.vue -->
<template>
  <section id="contacto" class="py-16 md:py-32 bg-[#0A0F1E]">
    <div class="container mx-auto px-4 sm:px-6">
      <!-- Contenedor principal con animación de entrada -->
      <div 
        class="relative backdrop-blur-xl bg-gradient-to-br from-white/5 to-white/2 rounded-3xl md:rounded-[4rem] overflow-hidden border border-white/10 shadow-2xl shadow-orange-500/10"
        :style="{
          animation: 'slideUp 0.6s cubic-bezier(0.4, 0, 0.2, 1)',
        }"
      >
        <div class="grid lg:grid-cols-2">
          
          <!-- Columna izquierda - Información -->
          <div class="p-6 sm:p-8 lg:p-12 xl:p-20 bg-[#0F1428] text-white flex flex-col justify-between relative overflow-hidden">
            <!-- Efecto de gradiente animado -->
            <div 
              class="absolute inset-0 bg-gradient-to-r from-orange-500/5 via-transparent to-blue-500/5"
              :style="{
                animation: 'gradientShift 8s ease-in-out infinite',
              }"
            ></div>
            
            <!-- Icono decorativo flotante -->
            <div class="absolute top-4 right-4 sm:top-8 sm:right-8 opacity-5">
              <svg class="w-24 h-24 sm:w-32 sm:h-32 md:w-40 md:h-40" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/>
              </svg>
            </div>
            
            <div class="relative z-10">
              <!-- Título con animación de texto -->
              <h2 class="text-3xl sm:text-4xl md:text-5xl font-black mb-6 sm:mb-8 tracking-tight animate-slideUp">
                HABLEMOS <br /> 
                DE <span class="text-[#FF5F00] italic animate-pulse">INGENIERÍA.</span>
              </h2>
              
              <!-- Descripción -->
              <p class="text-gray-400 text-lg sm:text-xl mb-8 sm:mb-12 md:mb-16 max-w-sm">
                Su estación merece el mejor respaldo técnico. Escríbanos hoy mismo.
              </p>
              
              <!-- Información de contacto -->
              <div class="space-y-6 sm:space-y-8 md:space-y-10">
                <ContactItem 
                  v-for="(item, index) in contactInfo"
                  :key="index"
                  :item="item"
                  :index="index"
                />
              </div>
            </div>

            <!-- Footer -->
            <div class="mt-12 sm:mt-16 md:mt-20 pt-6 sm:pt-8 md:pt-10 border-t border-white/5">
              <p class="text-gray-500 text-xs font-medium uppercase tracking-widest">
                PETROFIX S.A.S. © 2024 • OIL & GAS DIVISION
              </p>
            </div>
          </div>

          <!-- Columna derecha - Formulario -->
          <div class="p-6 sm:p-8 lg:p-12 xl:p-20 bg-dark/50">
            <form @submit.prevent="handleSubmit" class="space-y-6 sm:space-y-8">
              <!-- Campo Nombre -->
              <FormField
                label="Nombre Completo"
                type="text"
                placeholder="Ej. Juan Pérez"
                v-model="formData.nombre"
                required
              />
              
              <!-- Campos Email y Celular -->
              <div class="grid md:grid-cols-2 gap-6 sm:gap-8 md:gap-12">
                <FormField
                  label="Email"
                  type="email"
                  placeholder="juan@empresa.com"
                  v-model="formData.email"
                  required
                />
                <FormField
                  label="Celular"
                  type="tel"
                  placeholder="300 123 4567"
                  v-model="formData.celular"
                  required
                />
              </div>

              <!-- Campo Mensaje -->
              <div class="group">
                <label class="block text-xs font-black uppercase tracking-widest text-gray-500 mb-2 sm:mb-3 group-focus-within:text-[#FF5F00] transition-colors duration-300">
                  Mensaje
                </label>
                <textarea 
                  rows="3"
                  required
                  class="w-full bg-[#0F1428] border-b-2 border-white/10 px-0 py-3 sm:py-4 focus:border-[#FF5F00] outline-none transition-all duration-300 text-lg sm:text-xl font-bold placeholder:text-white/5 resize-none hover:border-orange-500/30"
                  placeholder="Cuéntanos tu requerimiento..."
                  v-model="formData.mensaje"
                ></textarea>
              </div>

              <!-- Checkbox Política -->
              <div class="flex items-start gap-3 sm:gap-4 py-4">
                <input 
                  type="checkbox" 
                  id="policy" 
                  required 
                  class="mt-1 w-5 h-5 sm:w-6 sm:h-6 rounded border-white/10 bg-[#0F1428] text-[#FF5F00] focus:ring-2 focus:ring-[#FF5F00] cursor-pointer transition-all hover:scale-110"
                />
                <label for="policy" class="text-sm text-gray-500 font-medium">
                  Acepto la 
                  <button 
                    type="button" 
                    @click="showModal = true"
                    class="text-white underline font-bold hover:text-[#FF5F00] transition-colors"
                  >
                    Política de Datos
                  </button>
                </label>
              </div>

              <!-- Botón de envío -->
              <button 
                type="submit"
                class="w-full bg-gradient-to-r from-[#FF5F00] to-[#FF8C00] text-white py-4 sm:py-5 md:py-6 rounded-2xl font-black text-lg sm:text-xl md:text-2xl hover:shadow-[0_20px_50px_-10px_rgba(255,95,0,0.4)] transition-all duration-300 flex items-center justify-center gap-3 sm:gap-4 group active:scale-[0.98]"
                :style="{
                  animation: 'pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite',
                }"
              >
                <span class="group-hover:translate-x-1 transition-transform duration-300">
                  ENVIAR SOLICITUD
                </span>
                <svg class="w-5 h-5 sm:w-6 sm:h-6 group-hover:rotate-45 transition-transform duration-300" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 19l9 2-9-18-9 18 9-2zm0 0v-8"/>
                </svg>
              </button>
            </form>
          </div>
        </div>
      </div>
    </div>

    <!-- Modal de Política -->
    <ModalPolicy 
      v-if="showModal" 
      @close="showModal = false" 
    />
  </section>
</template>

<script setup>
import { ref, reactive } from 'vue'

// Estado del formulario
const formData = reactive({
  nombre: '',
  email: '',
  celular: '',
  mensaje: ''
})

// Estado del modal
const showModal = ref(false)

// Información de contacto
const contactInfo = [
  {
    icon: `<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"/>
          </svg>`,
    label: 'Línea Directa',
    value: '+57 316 665 5551'
  },
  {
    icon: `<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/>
          </svg>`,
    label: 'Correo Técnico',
    value: 'proyectos@petrofix.com.co'
  },
  {
    icon: `<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"/>
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"/>
          </svg>`,
    label: 'HQ Medellín',
    value: 'Calle 28 N 65 C 65'
  }
]

// Componente para ítems de contacto
const ContactItem = {
  props: ['item', 'index'],
  template: `
    <div 
      class="flex items-center gap-4 sm:gap-6 group cursor-pointer transform transition-all duration-300 hover:translate-x-2"
      :style="{
        animation: 'slideRight 0.5s ease-out ' + (index * 0.1) + 's both'
      }"
    >
      <div 
        class="w-12 h-12 sm:w-14 sm:h-14 bg-white/5 rounded-2xl flex items-center justify-center text-[#FF5F00] group-hover:bg-gradient-to-br group-hover:from-[#FF5F00] group-hover:to-[#FF8C00] group-hover:text-white transition-all duration-300 shadow-lg group-hover:shadow-orange-500/30"
      >
        <div v-html="item.icon"></div>
      </div>
      <div>
        <p class="text-gray-500 text-xs font-bold uppercase tracking-widest mb-1">{{ item.label }}</p>
        <p class="text-lg sm:text-xl font-bold group-hover:text-[#FF5F00] transition-colors duration-300">{{ item.value }}</p>
      </div>
    </div>
  `
}

// Componente para campos del formulario
const FormField = {
  props: ['label', 'type', 'placeholder', 'modelValue', 'required'],
  emits: ['update:modelValue'],
  template: `
    <div class="group">
      <label class="block text-xs font-black uppercase tracking-widest text-gray-500 mb-2 sm:mb-3 group-focus-within:text-[#FF5F00] transition-colors duration-300">
        {{ label }}
      </label>
      <input 
        :type="type"
        :required="required"
        class="w-full bg-[#0F1428] border-b-2 border-white/10 px-0 py-3 sm:py-4 focus:border-[#FF5F00] outline-none transition-all duration-300 text-lg sm:text-xl font-bold placeholder:text-white/5 hover:border-orange-500/30"
        :placeholder="placeholder"
        :value="modelValue"
        @input="$emit('update:modelValue', $event.target.value)"
      />
    </div>
  `
}

// Componente Modal
const ModalPolicy = {
  props: ['show'],
  emits: ['close'],
  template: `
    <div 
      class="fixed inset-0 z-[200] flex items-center justify-center p-4 bg-black/90 backdrop-blur-xl"
      :style="{
        animation: 'fadeIn 0.3s ease-out'
      }"
      @click.self="$emit('close')"
    >
      <div 
        class="bg-[#0F1428] rounded-3xl p-6 sm:p-8 md:p-12 max-w-2xl w-full border border-white/10 relative shadow-2xl shadow-orange-500/20"
        :style="{
          animation: 'scaleUp 0.4s cubic-bezier(0.4, 0, 0.2, 1)'
        }"
      >
        <!-- Botón cerrar -->
        <button 
          @click="$emit('close')"
          class="absolute top-4 right-4 sm:top-6 sm:right-6 text-gray-400 hover:text-white transition-colors"
        >
          <svg class="w-6 h-6 sm:w-8 sm:h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
          </svg>
        </button>
        
        <!-- Título -->
        <h3 class="text-2xl sm:text-3xl font-black text-white mb-6 sm:mb-8 tracking-tight">
          POLÍTICA DE PRIVACIDAD
        </h3>
        
        <!-- Contenido -->
        <div class="text-gray-400 space-y-4 sm:space-y-6 text-base sm:text-lg max-h-[50vh] overflow-y-auto pr-4 custom-scrollbar">
          <p>PETROFIX S.A.S. garantiza la protección de datos bajo la Ley 1581 de 2012.</p>
          <p>Sus datos solo se usarán para fines comerciales y técnicos directos de nuestra operación.</p>
          <p>No compartimos información con terceros sin su consentimiento explícito.</p>
        </div>
        
        <!-- Botón aceptar -->
        <button 
          @click="$emit('close')"
          class="mt-8 sm:mt-12 w-full py-3 sm:py-4 bg-white text-[#0A0F1E] rounded-2xl font-black text-lg sm:text-xl hover:bg-gradient-to-r hover:from-[#FF5F00] hover:to-[#FF8C00] hover:text-white transition-all duration-300 transform hover:scale-[1.02] active:scale-[0.98]"
        >
          COMPRENDIDO
        </button>
      </div>
    </div>
  `
}

// Función de envío del formulario
const handleSubmit = () => {
  alert('¡Gracias! Su requerimiento técnico ha sido recibido.')
  // Resetear formulario
  Object.keys(formData).forEach(key => {
    formData[key] = ''
  })
}
</script>

<style scoped>
/* Animaciones inline sin CSS externo */
@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes slideRight {
  from {
    opacity: 0;
    transform: translateX(-20px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

@keyframes scaleUp {
  from {
    opacity: 0;
    transform: scale(0.9);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}

@keyframes gradientShift {
  0%, 100% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
}

@keyframes pulse {
  0%, 100% {
    box-shadow: 0 20px 40px -10px rgba(255, 95, 0, 0.3);
  }
  50% {
    box-shadow: 0 20px 60px -10px rgba(255, 95, 0, 0.5);
  }
}

/* Scrollbar personalizado */
.custom-scrollbar::-webkit-scrollbar {
  width: 6px;
}

.custom-scrollbar::-webkit-scrollbar-track {
  background: transparent;
}

.custom-scrollbar::-webkit-scrollbar-thumb {
  background: rgba(255, 95, 0, 0.5);
  border-radius: 3px;
}

.custom-scrollbar::-webkit-scrollbar-thumb:hover {
  background: rgba(255, 95, 0, 0.7);
}
</style>