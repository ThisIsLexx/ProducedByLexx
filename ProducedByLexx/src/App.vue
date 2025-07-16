<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import { ref } from 'vue'
import { Transition } from 'vue'
import Servicio from './components/Servicio.vue'
import ReproductorMp3 from './components/ReproductorMp3.vue'

const scrollTo = (id: string) => {
  const element = document.querySelector(id);
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' });
  }
};

</script>

<template>

  <div class="max-h-screen overflow-y-auto no-scrollbar mx-auto px-2">

    <!-- BEGIN: NAVBAR -->
    <div class="absolute inset-0 -z-10 overflow-hidden">
      <div
        class="absolute w-[300px] h-[300px] bg-[#00ffd1] rounded-full blur-[120px] opacity-30 top-6 left-12 animate-float">
      </div>
      <div
        class="absolute w-[400px] h-[400px] bg-[#ff5c00] rounded-full blur-[160px] opacity-25 top-[60%] left-[65%] animate-float">
      </div>
      <div
        class="absolute w-[250px] h-[250px] bg-[#ff00ff] rounded-full blur-[100px] opacity-20 top-[80%] left-[10%] animate-float">
      </div>
    </div>


    <nav class="text-white py-4 absolute top-0 left-6 right-6 z-10 backdrop-blur-md">
      <div class="flex px-4 items-center justify-between">
        <div class="flex items-center justify-end w-full">
          <div @click="scrollTo('#hero')"
            class="text-2xl font-bold text-[#00FFD1] hover:text-white hover:cursor-pointer transition-colors duration-300">
            L E X X
          </div>
        </div>
      </div>
    </nav>
    <!-- END: NAVBAR -->

    <!-- BEGIN: SECCIÓN HERO -->
    <section id="hero" class="flex flex-col gap-6 items-start h-[660px] justify-center text-white">
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
      <Transition :duration="{ enter: 10000, leave: 800 }" name="slide-fade" appear>
        <div class=" bg-[#FF5C00] text-white font-semibold px-6 py-3 rounded-md hover:bg-[#FF5C00]/80
        hover:cursor-pointer hover:scale-101 transition-all duration-100">
          Contactame!
        </div>
      </Transition>
    </section>
    <!-- END: HERO -->

    <!-- BEGIN: SOBRE MI -->
    <section class="h-100 w-full bg-gray-700/20 backdrop:blur-lg grid grid-cols-2 rounded-md overflow-auto">
      <div class="px-2 py-8 flex flex-col items-start w-full">
        <h2>
          <span class="text-4xl font-bold text-[#00FFD1] p-4">Sobre mí</span>
        </h2>
        <p class="text-gray-300 p-4 text-lg text-justify">
          Soy un productor musical con más de 10 años de experiencia en la industria. He trabajado con artistas de
          diversos géneros, ayudándoles a dar vida a sus ideas y proyectos musicales. Mi pasión por la música y mi
          compromiso con la calidad me impulsan a ofrecer servicios creativos que superen las expectativas.
        </p>
      </div>
      <div class="">
        IMAGEN MAMALONA
      </div>
    </section>
    <!-- END: SOBRE MI -->

    <!-- BEGIN: SERVICIOS -->
    <section class="h-100 !my-10">
      <div class="py-8 flex flex-col items-center w-full">
        <h2 class="text-4xl font-bold text-left text-[#00FFD1]">Servicios Disponibles</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4 w-full pt-4">
          <Servicio titulo="BEATMAKING" descripcion="Descripción de Producción Musical" />
          <Servicio titulo="MIX Y MASTERING" descripcion="Descripción de Producción Musical" />
          <Servicio titulo="PISTA SOBRE VOZ" descripcion="Descripción de Producción Musical" />
          <Servicio titulo="ASESORIAS CREATIVAS" descripcion="Descripción de Producción Musical" />
        </div>
      </div>

    </section>
    <!-- END: SERVICIOS -->

    <!-- BEGIN: PORTFOLIO -->
    <section class="h-100">
      <ReproductorMp3 />
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
