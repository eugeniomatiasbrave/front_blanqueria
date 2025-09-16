<script lang="ts">
  const API_URL = import.meta.env.VITE_BASE_URL;

  let name = '';
  let email = '';
  let phone = '';
  let message = '';
  let submitted = false;
  let loading = false;
  let error: string | null = null;
  let formErrors: Record<string, string> = {};
  

  async function handleSubmit() {
    loading = true;
    error = null;
    formErrors = {};
    
    try {
      const response = await fetch(`${API_URL}/api/contact`, {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({
          name,
          email,
          phone,
          message
        }),
      });
      
      const data = await response.json();
      
      if (!response.ok) {
        if (data.errors) {
          // Errores de validación del formulario
          formErrors = data.errors;
          error = 'Por favor corrija los errores en el formulario';
        } else {
          // Error general
          error = data.message || 'Error al enviar el formulario';
        }
        return;
      }
      
      // Éxito
      submitted = true;
      // Limpiar formulario
      name = '';
      email = '';
      phone = '';
      message = '';
    } catch (err) {
      error = 'Error de conexión con el servidor, por favor intente nuevamente';
      console.error('Error:', err);
    } finally {
      loading = false;
    }
  }
</script>

<section id="contacto" class="section bg-gray-50">
  <div class="container">
    <div class="max-w-3xl mx-auto">
      <div class="text-center mb-12">
        <h2 class="text-3xl md:text-4xl font-bold text-gray-800 mb-4">Contáctanos hoy mismo</h2>
        <p class="text-gray-600">Estamos aquí para responder tus preguntas y ayudarte a encontrar los textiles perfectos para tu hogar.</p>
      </div>
      
      {#if submitted}
        <div class="bg-green-50 border-l-4 border-green-500 p-6 rounded-lg mb-8">
          <div class="flex items-center">
            <div class="flex-shrink-0">
              <svg class="h-8 w-8 text-green-500" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
              </svg>
            </div>
            <div class="ml-4">
              <h3 class="text-lg font-semibold text-green-700">¡Mensaje enviado con éxito!</h3>
              <p class="text-green-600 mt-1">Gracias por contactarnos. Te responderemos a la brevedad.</p>
              <button 
                class="mt-3 text-green-700 font-medium underline"
                on:click={() => submitted = false}
              >
                Enviar otro mensaje
              </button>
            </div>
          </div>
        </div>
      {:else}
        <form 
          class="bg-white p-8 rounded-xl shadow-sm"
          on:submit|preventDefault={handleSubmit}
        >
          {#if error}
            <div class="bg-red-50 border-l-4 border-red-500 p-4 rounded-md mb-6">
              <p class="text-red-700">{error}</p>
            </div>
          {/if}
          
          <div class="mb-6">
            <label for="name" class="block text-gray-700 font-medium mb-2">Nombre completo*</label>
            <input 
              type="text" 
              id="name" 
              bind:value={name}
              class="w-full px-4 py-3 border {formErrors.name ? 'border-red-500' : 'border-gray-300'} rounded-lg focus:ring-2 focus:ring-primary focus:border-primary transition-colors"
              placeholder="Tu nombre"
              required
            />
            {#if formErrors.name}
              <p class="text-red-500 text-sm mt-1">{formErrors.name}</p>
            {/if}
          </div>
          
          <div class="mb-6">
            <label for="email" class="block text-gray-700 font-medium mb-2">Correo electrónico*</label>
            <input 
              type="email" 
              id="email" 
              bind:value={email}
              class="w-full px-4 py-3 border {formErrors.email ? 'border-red-500' : 'border-gray-300'} rounded-lg focus:ring-2 focus:ring-primary focus:border-primary transition-colors"
              placeholder="tucorreo@ejemplo.com"
              required
            />
            {#if formErrors.email}
              <p class="text-red-500 text-sm mt-1">{formErrors.email}</p>
            {/if}
          </div>
          
          <div class="mb-6">
            <label for="phone" class="block text-gray-700 font-medium mb-2">Teléfono (opcional)</label>
            <input 
              type="tel" 
              id="phone" 
              bind:value={phone}
              class="w-full px-4 py-3 border {formErrors.phone ? 'border-red-500' : 'border-gray-300'} rounded-lg focus:ring-2 focus:ring-primary focus:border-primary transition-colors"
              placeholder="Tu número de teléfono"
            />
            {#if formErrors.phone}
              <p class="text-red-500 text-sm mt-1">{formErrors.phone}</p>
            {/if}
          </div>
          
          <div class="mb-6">
            <label for="message" class="block text-gray-700 font-medium mb-2">Mensaje*</label>
            <textarea 
              id="message" 
              bind:value={message}
              class="w-full px-4 py-3 border {formErrors.message ? 'border-red-500' : 'border-gray-300'} rounded-lg focus:ring-2 focus:ring-primary focus:border-primary transition-colors"
              rows="4"
              placeholder="¿En qué podemos ayudarte?"
              required
            ></textarea>
            {#if formErrors.message}
              <p class="text-red-500 text-sm mt-1">{formErrors.message}</p>
            {/if}
          </div>
          
          <div class="mb-6">
            <label class="flex items-center">
              <input type="checkbox" class="h-5 w-5 text-primary rounded focus:ring-primary" required />
              <span class="ml-2 text-gray-600">
                Acepto la <a href="/politica-privacidad" class="text-primary hover:underline">política de privacidad</a>
              </span>
            </label>
          </div>
          
          <button 
            type="submit" 
            class="w-full btn-primary py-4 flex items-center justify-center"
            disabled={loading}
          >
            {#if loading}
              <svg class="animate-spin -ml-1 mr-3 h-5 w-5 text-white" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
                <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
              </svg>
              Enviando...
            {:else}
              Enviar mensaje
            {/if}
          </button>
        </form>
      {/if}
      
      <div class="mt-12 grid md:grid-cols-3 gap-8 text-center">
        <div>
          <div class="w-12 h-12 bg-primary/10 rounded-full flex items-center justify-center mx-auto mb-4">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
            </svg>
          </div>
          <h3 class="font-medium text-gray-800 mb-1">Teléfono</h3>
          <p class="text-gray-600">+54 11 5678-9012</p>
        </div>
        
        <div>
          <div class="w-12 h-12 bg-primary/10 rounded-full flex items-center justify-center mx-auto mb-4">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
            </svg>
          </div>
          <h3 class="font-medium text-gray-800 mb-1">Email</h3>
          <p class="text-gray-600">info@blanqueria.com</p>
        </div>
        
        <div>
          <div class="w-12 h-12 bg-primary/10 rounded-full flex items-center justify-center mx-auto mb-4">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
            </svg>
          </div>
          <h3 class="font-medium text-gray-800 mb-1">Dirección</h3>
          <p class="text-gray-600">Av. Principal 123, Buenos Aires</p>
        </div>
      </div>
    </div>
  </div>
</section>