<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import { ref } from 'vue'
import { Transition } from 'vue'

const currentlyPlaying = ref(0)
const curretlyPlaying = (songId: number) => {
  currentlyPlaying.value = songId
}

</script>

<template>

  <div class="max-h-screen overflow-y-auto no-scrollbar mx-auto px-2">

    <!-- BEGIN: NAVBAR -->
    <div class="absolute inset-0 -z-10 overflow-hidden">
      <div class="absolute w-[300px] h-[300px] bg-[#00ffd1] rounded-full blur-[120px] opacity-30 top-6 left-12 animate-float"></div>
      <div class="absolute w-[400px] h-[400px] bg-[#ff5c00] rounded-full blur-[160px] opacity-25 top-[60%] left-[65%] animate-float"></div>
      <div class="absolute w-[250px] h-[250px] bg-[#ff00ff] rounded-full blur-[100px] opacity-20 top-[80%] left-[10%] animate-float"></div>
    </div>
    
  
    <nav class="text-white py-4 absolute top-0 left-6 right-6 z-10 backdrop-blur-md">
      <div class="flex px-4 items-center justify-between">
        <div class="flex items-center justify-end w-full">
          <div to="/" class="text-2xl font-bold text-[#00FFD1] hover:text-white hover:cursor-pointer transition-colors duration-300">
            L E X X
          </div>
        </div>
      </div>
    </nav>
    <!-- END: NAVBAR -->
  
      <!-- BEGIN: SECCIÓN HERO -->
      <section class="flex flex-col gap-6 items-start h-[660px] justify-center text-white">
          <Transition name="slide-fade" appear>
            <h1 class="text-8xl font-bold mb- text-[#00FFD1]">
              Convierte tu idea en un proyecto
            </h1>
          </Transition>
          <Transition name="slide-fade" appear style="transition-delay: 0.4s;">
            <p class="text-2xl font-semibold mb-6 mt-2 text-gray-300">
              Producción musical y servicios creativos
            </p>
          </Transition>
          <Transition name="slide-fade" appear>
            <div class="bg-[#FF5C00] text-white font-semibold px-6 py-3 rounded-md hover:bg-[#FF5C00]/80 hover:cursor-pointer hover:scale-101 transition-all duration-100">
              Comienza tu proyecto
            </div>
          </Transition>
      </section>
      <!-- END: HERO -->
       
      <!-- BEGIN: SOBRE MI -->
      <section>
        <div class="px-4 py-8 flex flex-col ">
  
        </div>
      </section>
      <!-- END: SOBRE MI -->
  
      <!-- BEGIN: SERVICIOS -->
      <section class="h-100">
          <div class="px-4 py-8 flex flex-col items-center w-full">
              <h2 class="text-4xl font-bold pb-2 text-center text-[#00FFD1]">Servicios Disponibles</h2>
              <div class="h-[1px] bg-white/60 backdrop-blur-xs w-full"></div>
              <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4 w-full pt-4">
                  <div class="bg-gray-800 p-6 rounded-lg shadow-md hover:shadow-lg hover:scale-101 transition-all duration-100 ease-linear">
                      <h3 class="text-xl w-full flex justify-center font-semibold mb-2 text-[#00FFD1]">BEATMAKING</h3>
                      <p class="text-gray-700">DESCRIPCIÓN</p>
                  </div>
                  <div class="bg-gray-800 p-6 rounded-lg shadow-md hover:shadow-lg hover:scale-101 transition-all duration-100 ease-linear">
                      <h3 class="text-xl w-full flex justify-center font-semibold mb-2 text-[#00FFD1]">MEZCLA Y MASTERING</h3>
                      <p class="text-gray-700">DESCRIPCIÓN</p>
                  </div>
                  <div class="bg-gray-800 p-6 rounded-lg shadow-md hover:shadow-lg hover:scale-101 transition-all duration-100 ease-linear">
                      <h3 class="text-xl w-full flex justify-center font-semibold mb-2 text-[#00FFD1]">PISTA SOBRE VOZ</h3>
                      <p class="text-gray-700">DESCRIPCIÓN</p>
                  </div>
                  <div class="bg-gray-800 p-6 rounded-lg shadow-md hover:shadow-lg hover:scale-101 transition-all duration-100 ease-linear">
                      <h3 class="text-xl w-full flex justify-center font-semibold mb-2 text-[#00FFD1]">ASESORIA CREATIVA</h3>
                      <p class="text-gray-700">DESCRIPCIÓN</p>
                  </div>
              </div>
          </div>
  
      </section>
      <!-- END: SERVICIOS -->
  
      <!-- BEGIN: PORTFOLIO -->
      <section class="h-100">
          <div class="px-4 py-8 flex flex-col items-center w-full">
              <h2 class="text-4xl font-bold mb-6 text-left w-full text-[#00FFD1]">Portafolio</h2>
              <div class="w-full flex flex-col gap-2 pt-4">
                <div v-if="currentlyPlaying == 1" :class="currentlyPlaying == 1 ? 'h-16' : ''" class="w-full p-4 h-12 flex justify-start items-center rounded-md bg-gray-800 hover:bg-gray-700 transition-all duration-200 ease-linear">
                  CANCIÓN 1
                </div>
                <div v-else v-on:click="curretlyPlaying(1)" class="w-full p-4 h-12 flex justify-start items-center rounded-md bg-gray-800 hover:bg-gray-700 transition-all duration-200 ease-linear">
                  CANCIÓN 1 (PULSA PARA REPRODUCIR)
                </div>
                <div v-if="currentlyPlaying == 2" :class="currentlyPlaying == 2 ? 'h-16' : ''" class="w-full p-4 h-12 flex justify-start items-center rounded-md bg-gray-800 hover:bg-gray-700 transition-all duration-200 ease-linear">
                  CANCIÓN 2
                </div>
                <div v-else v-on:click="curretlyPlaying(2)" class="w-full p-4 h-12 flex justify-start items-center rounded-md bg-gray-800 hover:bg-gray-700 transition-all duration-200 ease-linear">
                  CANCIÓN 2 (PULSA PARA REPRODUCIR)
                </div>
                <div v-if="currentlyPlaying == 3" :class="currentlyPlaying == 3 ? 'h-16' : ''" class="w-full p-4 h-12 flex justify-start items-center rounded-md bg-gray-800 hover:bg-gray-700 transition-all duration-200 ease-linear">
                  CANCIÓN 3
                </div>
                <div v-else v-on:click="curretlyPlaying(3)" class="w-full p-4 h-12 flex justify-start items-center rounded-md bg-gray-800 hover:bg-gray-700 transition-all duration-200 ease-linear">
                  CANCIÓN 3 (PULSA PARA REPRODUCIR)
                </div>
            
  
              </div>
          </div>
      </section>
      <!-- END: PORTFOLIO -->
  
      <!-- BEGIN: TESTIMONIOS -->
      <section class="h-100">
          <div class="px-4 py-8 flex flex-col items-center w-full">
              <h2 class="text-4xl font-bold mb-6 text-left w-full text-[#00FFD1]">Testimonios</h2>
          </div>
      </section>
      <!-- END: TESTIMONIOS -->
  
      <!-- BEGIN: CONTACTO -->
      <section class="h-100">
          <div class="px-4 py-8 flex flex-col items-center w-full">
              <h2 class="text-4xl font-bold mb-6 text-left w-full text-[#00FFD1]">Contacto</h2>
          </div>
      </section>
      <!-- END: CONTACTO -->
  
    </div>
    <!-- BEGIN: FOOTER -->
   <footer class="justify-self-end text-white py-4 bg-white/5 rounded-md absolute bottom-5 right-6">
       <div class="flex px-4 items-center justify-end gap-4">
           <p>
              <a href="https://www.instagram.com/produc3dbylexx/" class="text-[#00FFD1] hover:underline">INSTAGRAM</a>
              <a href="https://www.youtube.com/@ThisIsLexx" class="text-[#00FFD1] hover:underline">YOUTUBE</a>
           </p>
           <p>&copy; 2025 ThisIsLexx. Todos los derechos reservados.</p>
       </div>
   </footer>
   <!-- END: FOOTER -->
    
</template>

<style scoped>

.slide-fade-enter-active {
  transition: all 0.8s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(20px);
  opacity: 0;
}

</style>