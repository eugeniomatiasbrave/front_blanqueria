<script lang="ts">
  let isMenuOpen = false;
  
  function toggleMenu() {
    isMenuOpen = !isMenuOpen;
  }
</script>

<header class="bg-white shadow-sm py-4 sticky top-0 z-50">
  <div class="container flex justify-between items-center">
    <a href="/" class="font-heading text-2xl font-bold text-primary">Blanquería</a>
    
    <button 
      class="md:hidden text-gray-700"
      on:click={toggleMenu}
      aria-label={isMenuOpen ? 'Cerrar menú' : 'Abrir menú'}
    >
      <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        {#if isMenuOpen}
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
        {:else}
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
        {/if}
      </svg>
    </button>
    
    <nav class={`${isMenuOpen ? 'block' : 'hidden'} md:block absolute md:relative top-full left-0 w-full md:w-auto bg-white md:bg-transparent shadow-md md:shadow-none`}>
      <ul class="flex flex-col md:flex-row px-4 py-4 md:py-0 md:px-0 space-y-3 md:space-y-0 md:space-x-6">
        <li><a href="#productos" class="block text-gray-700 hover:text-primary font-medium">Productos</a></li>
        <li><a href="#beneficios" class="block text-gray-700 hover:text-primary font-medium">Beneficios</a></li>
        <li><a href="#testimonios" class="block text-gray-700 hover:text-primary font-medium">Testimonios</a></li>
        <li><a href="#contacto" class="block text-gray-700 hover:text-primary font-medium">Contacto</a></li>
      </ul>
    </nav>
  </div>
</header> 