<script>
  const products = [
    {
      id: 1,
      name: 'Juego de Sábanas Premium',
      description: 'Juego completo con 4 piezas de algodón egipcio de 400 hilos.',
      price: 129.99,
      image: 'https://images.unsplash.com/photo-1522771739844-6a9f6d5f14af?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1471&q=80'
    },
    {
      id: 2,
      name: 'Set de Toallas Ultra Suaves',
      description: 'Set de 3 toallas de diferentes tamaños, 100% algodón de alta absorción.',
      price: 79.99,
      image: 'https://images.unsplash.com/photo-1563453392212-326f5e854473?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80'
    },
    {
      id: 3,
      name: 'Cortinas Elegantes',
      description: 'Par de cortinas con aislante térmico, perfectas para cualquier habitación.',
      price: 149.99,
      image: 'https://images.unsplash.com/photo-1513694203232-719a280e022f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1469&q=80'
    },
    {
      id: 4,
      name: 'Edredón de Plumas',
      description: 'Edredón premium con relleno hipoalergénico, para todas las estaciones.',
      price: 199.99,
      image: 'https://images.unsplash.com/photo-1562184552-997c461abbe6?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1458&q=80'
    }
  ];
</script>

<section id="productos" class="section bg-gray-50">
  <div class="container">
    <div class="text-center mb-16">
      <h2 class="text-3xl md:text-4xl font-bold text-gray-800 mb-4">Nuestros Productos Destacados</h2>
      <p class="text-gray-600 max-w-2xl mx-auto">Descubre la colección de textiles que transformarán tus espacios con elegancia y confort.</p>
    </div>
    
    <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
      {#each products as product}
        <div class="bg-white rounded-xl shadow-sm overflow-hidden hover:shadow-md transition-shadow">
          <div class="aspect-w-4 aspect-h-3">
            <img 
              src={product.image} 
              alt={product.name}
              class="w-full h-64 object-cover" 
              loading="lazy"
            />
          </div>
          <div class="p-6">
            <h3 class="text-xl font-bold text-gray-800 mb-2">{product.name}</h3>
            <p class="text-gray-600 mb-4">{product.description}</p>
            <div class="flex items-center justify-between">
              <span class="text-xl font-bold text-primary">${product.price}</span>
              <a href="#contacto" class="btn-primary py-2 px-4">Comprar</a>
            </div>
          </div>
        </div>
      {/each}
    </div>
    
    <div class="text-center mt-12">
      <a href="#contacto" class="btn-primary">Ver catálogo completo</a>
    </div>
  </div>
</section> 