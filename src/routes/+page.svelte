<script>
  import Header from '$lib/components/Header.svelte';
  import Hero from '$lib/components/Hero.svelte';
  import Benefits from '$lib/components/Benefits.svelte';
  import Products from '$lib/components/Products.svelte';
  import Testimonials from '$lib/components/Testimonials.svelte';
  import Contact from '$lib/components/Contact.svelte';
  import Footer from '$lib/components/Footer.svelte';
</script>

<svelte:head>
  <title>Blanquería Premium - Textiles de calidad para tu hogar</title>
  <meta name="description" content="Sábanas, toallas y cortinas que combinan estilo y confort para dar vida a tu hogar con textiles de calidad premium." />
</svelte:head>

<Header />
<main>
  <Hero />
  <Benefits />
  <Products />
  <Testimonials />
  <Contact />
</main>
<Footer /> 