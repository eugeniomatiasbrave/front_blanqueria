<script>
  const testimonials = [
    {
      id: 1,
      name: 'Laura Martínez',
      position: 'Cliente desde 2021',
      content: 'Las sábanas son increíblemente suaves y después de múltiples lavados siguen manteniendo su calidad. Sin duda, la mejor inversión para mi dormitorio.',
      image: 'https://randomuser.me/api/portraits/women/24.jpg'
    },
    {
      id: 2,
      name: 'Carlos Rodríguez',
      position: 'Cliente desde 2020',
      content: 'Mi familia y yo estamos encantados con las toallas. Su capacidad de absorción es impresionante y no pierden suavidad con el tiempo. Totalmente recomendables.',
      image: 'https://randomuser.me/api/portraits/men/36.jpg'
    },
    {
      id: 3,
      name: 'Elena García',
      position: 'Cliente desde 2022',
      content: 'El servicio al cliente es excepcional. Tuve un pequeño problema con mi pedido y lo resolvieron inmediatamente. Además, la calidad de sus cortinas es inmejorable.',
      image: 'https://randomuser.me/api/portraits/women/67.jpg'
    }
  ];
</script>

<section id="testimonios" class="section bg-white">
  <div class="container">
    <div class="text-center mb-16">
      <h2 class="text-3xl md:text-4xl font-bold text-gray-800 mb-4">Lo que dicen nuestros clientes</h2>
      <p class="text-gray-600 max-w-2xl mx-auto">Experiencias reales de quienes ya disfrutan de nuestros productos en sus hogares.</p>
    </div>
    
    <div class="grid md:grid-cols-3 gap-8">
      {#each testimonials as testimonial}
        <div class="bg-gray-50 p-8 rounded-xl shadow-sm hover:shadow-md transition-shadow relative">
          <div class="absolute -top-5 left-8 bg-primary text-white rounded-full w-10 h-10 flex items-center justify-center">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 8h10M7 12h4m1 8l-4-4H5a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v8a2 2 0 01-2 2h-3l-4 4z" />
            </svg>
          </div>
          
          <div class="mb-6 mt-4">
            <p class="text-gray-600 italic">"{testimonial.content}"</p>
          </div>
          
          <div class="flex items-center">
            <img 
              src={testimonial.image} 
              alt={testimonial.name}
              class="w-12 h-12 rounded-full mr-4" 
              loading="lazy"
            />
            <div>
              <h4 class="font-bold text-gray-800">{testimonial.name}</h4>
              <p class="text-gray-500 text-sm">{testimonial.position}</p>
            </div>
          </div>
        </div>
      {/each}
    </div>
    
    <div class="mt-16 text-center">
      <div class="inline-flex items-center bg-gray-100 px-6 py-3 rounded-lg">
        <span class="text-gray-700 font-medium mr-2">Calificación promedio:</span>
        <div class="flex text-yellow-400">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
            <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
          </svg>
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
            <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
          </svg>
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
            <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
          </svg>
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
            <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
          </svg>
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
            <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
          </svg>
        </div>
        <span class="font-bold text-gray-800 ml-2">5.0</span>
        <span class="text-gray-500 ml-2">(127 reseñas)</span>
      </div>
    </div>
  </div>
</section> 