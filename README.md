```html
<!DOCTYPE html>
<html lang="es" class="scroll-smooth">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Arena's Hotel &amp; Restaurant | Mariscos, Parrilla y Estadía</title>
  <meta name="description" content="Menú digital oficial y reservas de Arena's Hotel & Restaurant. Mariscos frescos, carnes a la parrilla, bebidas y descanso frente al mar en Honduras." />

  <!-- Tailwind CSS -->
  <script src="https://cdn.tailwindcss.com"></script>

  <!-- Google Fonts: Fredoka (títulos estilo marca), Outfit y Plus Jakarta Sans -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@600;700&family=Outfit:wght@500;600;700;800&family=Plus+Jakarta+Sans:wght@400;500;600;700&display=swap" rel="stylesheet" />

  <!-- Configuración personalizada de Tailwind con la paleta oficial -->
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            slateDark: '#121619',
            slateCard: '#1A2026',
            slateElevated: '#222A32',
            coral: '#F25C19',
            coralHover: '#D94B0D',
            marine: '#1868B7',
            turquoise: '#0099DB',
            crimson: '#B71C1C',
          },
          fontFamily: {
            brand: ['Fredoka', 'Outfit', 'sans-serif'],
            display: ['Outfit', 'sans-serif'],
            sans: ['Plus Jakarta Sans', 'sans-serif'],
          },
          boxShadow: {
            'coral-glow': '0 10px 30px -5px rgba(242, 92, 25, 0.35)',
            'ocean-glow': '0 10px 30px -5px rgba(0, 153, 219, 0.28)',
          }
        }
      }
    };
  </script>

  <style>
    /* Textura sutil de pizarra oscura inspirada en el menú físico */
    body {
      background-color: #121619;
      background-image:
        radial-gradient(circle at 15% 15%, rgba(0, 153, 219, 0.08) 0%, transparent 42%),
        radial-gradient(circle at 85% 25%, rgba(242, 92, 25, 0.09) 0%, transparent 45%),
        radial-gradient(rgba(255, 255, 255, 0.025) 1px, transparent 0);
      background-size: 100% 100%, 100% 100%, 24px 24px;
      color: #F8FAFC;
    }

    /* Detalle decorativo tipo pincelada coral del menú físico */
    .coral-splash-border {
      position: relative;
    }
    .coral-splash-border::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      height: 4px;
      background: linear-gradient(90deg, #1868B7 0%, #0099DB 45%, #F25C19 100%);
    }

    /* Ocultar barra de scroll horizontal en filtros móviles */
    .no-scrollbar::-webkit-scrollbar {
      display: none;
    }
    .no-scrollbar {
      -ms-overflow-style: none;
      scrollbar-width: none;
    }

    /* Animación suave para el sticker del logotipo */
    @keyframes floatSticker {
      0%, 100% { transform: translateY(0px) rotate(0deg); }
      50% { transform: translateY(-6px) rotate(1deg); }
    }
    .logo-float {
      animation: floatSticker 5s ease-in-out infinite;
    }

    /* Estilo personalizado para selectores */
    select option {
      background-color: #1A2026;
      color: #F8FAFC;
    }
  </style>
</head>
<body class="font-sans antialiased selection:bg-coral selection:text-white">

  <!-- ===================================================================== -->
  <!-- BARRA DE NAVEGACIÓN FIJA (STICKY)                                     -->
  <!-- ===================================================================== -->
  <header class="sticky top-0 z-40 bg-slateDark/95 backdrop-blur-md border-b border-white/10 coral-splash-border">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-20">
        <!-- Logotipo y Nombre -->
        <a href="#inicio" class="flex items-center gap-3 group focus:outline-none">
          <div data-arenas-logo="sm" class="w-14 h-14 flex-shrink-0 transition-transform duration-300 group-hover:scale-105"></div>
          <div>
            <span class="block font-brand text-xl sm:text-2xl font-bold tracking-wide text-white leading-none">
              ARENA'S
            </span>
            <span class="block text-xs sm:text-sm font-semibold tracking-widest text-turquoise uppercase mt-0.5">
              Hotel &amp; Restaurant
            </span>
          </div>
        </a>

        <!-- Enlaces de Navegación (Desktop) -->
        <nav class="hidden lg:flex items-center gap-7 text-sm font-semibold text-slate-200">
          <a href="#inicio" class="hover:text-coral transition-colors">Inicio</a>
          <a href="#menu" class="hover:text-coral transition-colors">Menú</a>
          <a href="#encargos" class="hover:text-coral transition-colors flex items-center gap-1.5">
            <span>Solo por Encargo</span>
            <span class="w-2 h-2 rounded-full bg-coral animate-pulse"></span>
          </a>
          <a href="#hotel-reservas" class="hover:text-coral transition-colors">Hotel &amp; Reservas</a>
          <a href="#contacto" class="hover:text-coral transition-colors">Contacto</a>
        </nav>

        <!-- Acciones Derecha: Botón Mi Pedido + Menú Móvil -->
        <div class="flex items-center gap-3">
          <button
            type="button"
            onclick="toggleCartDrawer(true)"
            aria-label="Abrir Mi Pedido"
            class="relative inline-flex items-center gap-2.5 px-4 py-2.5 rounded-xl bg-coral hover:bg-coralHover text-white font-bold text-sm shadow-coral-glow transition-all active:scale-95 cursor-pointer"
          >
            <!-- Icono Bolsa/Pedido SVG -->
            <svg class="w-5 h-5" fill="none" stroke="currentColor" stroke-width="2.2" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M16 11V7a4 4 0 00-8 0v4M5 9h14l1 12H4L5 9z" />
            </svg>
            <span>Mi Pedido</span>
            <span
              id="nav-cart-count"
              class="inline-flex items-center justify-center min-w-[1.4rem] h-5 px-1.5 rounded-full bg-slateDark text-white text-xs font-extrabold"
            >
              0
            </span>
          </button>

          <!-- Botón Menú Hamburguesa (Móvil) -->
          <button
            type="button"
            id="mobile-menu-btn"
            onclick="toggleMobileMenu()"
            aria-label="Abrir menú de navegación"
            class="lg:hidden p-2.5 rounded-xl bg-slateCard border border-white/10 text-slate-200 hover:text-white hover:border-turquoise transition-colors"
          >
            <svg class="w-6 h-6" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16" />
            </svg>
          </button>
        </div>
      </div>
    </div>

    <!-- Menú Desplegable Móvil -->
    <div id="mobile-nav" class="hidden lg:hidden bg-slateCard border-t border-white/10 px-4 pt-3 pb-5 space-y-2">
      <a href="#inicio" onclick="toggleMobileMenu(false)" class="block px-3 py-2.5 rounded-xl text-base font-semibold text-slate-100 hover:bg-white/5 hover:text-coral">Inicio</a>
      <a href="#menu" onclick="toggleMobileMenu(false)" class="block px-3 py-2.5 rounded-xl text-base font-semibold text-slate-100 hover:bg-white/5 hover:text-coral">Menú Digital</a>
      <a href="#encargos" onclick="toggleMobileMenu(false)" class="block px-3 py-2.5 rounded-xl text-base font-semibold text-slate-100 hover:bg-white/5 hover:text-coral">Solo por Encargo</a>
      <a href="#hotel-reservas" onclick="toggleMobileMenu(false)" class="block px-3 py-2.5 rounded-xl text-base font-semibold text-slate-100 hover:bg-white/5 hover:text-coral">Hotel &amp; Reservas</a>
      <a href="#contacto" onclick="toggleMobileMenu(false)" class="block px-3 py-2.5 rounded-xl text-base font-semibold text-slate-100 hover:bg-white/5 hover:text-coral">Contacto</a>
    </div>
  </header>

  <!-- ===================================================================== -->
  <!-- SECCIÓN HERO                                                          -->
  <!-- ===================================================================== -->
  <section id="inicio" class="relative overflow-hidden pt-10 pb-16 sm:pt-16 sm:pb-24 border-b border-white/10">
    <!-- Resplandores ambientales de marca -->
    <div class="pointer-events-none absolute -top-24 -left-24 w-96 h-96 rounded-full bg-turquoise/15 blur-3xl"></div>
    <div class="pointer-events-none absolute top-1/2 -right-24 w-96 h-96 rounded-full bg-coral/15 blur-3xl"></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-10 lg:gap-8 items-center">
        <!-- Columna de Texto Principal -->
        <div class="lg:col-span-7 text-center lg:text-left space-y-6">
          <div class="inline-flex items-center gap-2 px-4 py-1.5 rounded-full bg-slateCard border border-turquoise/40 text-turquoise text-xs sm:text-sm font-bold tracking-wide uppercase">
            <span class="w-2 h-2 rounded-full bg-coral"></span>
            Sabor Costeño &amp; Hospitalidad en Honduras
          </div>

          <h1 class="font-display text-4xl sm:text-5xl lg:text-6xl font-extrabold tracking-tight text-white leading-[1.12]">
            Mariscos frescos, <span class="text-coral">carnes a la parrilla</span> y descanso frente al mar
          </h1>

          <p class="text-base sm:text-lg text-slate-300 max-w-2xl mx-auto lg:mx-0 leading-relaxed">
            Bienvenido a <strong class="text-white">Arena's Hotel &amp; Restaurant</strong>. Disfruta nuestros camarones al ajillo, pescado frito recién salido, alitas, parrilladas por encargo y habitaciones cómodas a pasos de la playa.
          </p>

          <!-- Botones de Acción Rápida -->
          <div class="flex flex-col sm:flex-row items-center justify-center lg:justify-start gap-4 pt-2">
            <a
              href="#menu"
              class="w-full sm:w-auto inline-flex items-center justify-center gap-2.5 px-7 py-4 rounded-2xl bg-coral hover:bg-coralHover text-white font-bold text-base shadow-coral-glow transition-all hover:-translate-y-0.5"
            >
              <span>Explorar Menú</span>
              <svg class="w-5 h-5" fill="none" stroke="currentColor" stroke-width="2.4" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" d="M19 9l-7 7-7-7" />
              </svg>
            </a>

            <a
              href="#hotel-reservas"
              class="w-full sm:w-auto inline-flex items-center justify-center gap-2.5 px-7 py-4 rounded-2xl bg-slateCard hover:bg-slateElevated text-white font-bold text-base border border-turquoise/50 shadow-ocean-glow transition-all hover:-translate-y-0.5"
            >
              <svg class="w-5 h-5 text-turquoise" fill="none" stroke="currentColor" stroke-width="2.2" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" />
              </svg>
              <span>Reservar / Encargar</span>
            </a>
          </div>

          <!-- Indicadores de servicio rápido -->
          <div class="grid grid-cols-3 gap-3 pt-4 max-w-lg mx-auto lg:mx-0">
            <div class="bg-slateCard/80 border border-white/10 rounded-xl p-3 text-center">
              <span class="block text-coral font-extrabold text-lg sm:text-xl">100%</span>
              <span class="text-xs text-slate-300 font-medium">Marisco Fresco</span>
            </div>
            <div class="bg-slateCard/80 border border-white/10 rounded-xl p-3 text-center">
              <span class="block text-turquoise font-extrabold text-lg sm:text-xl">WhatsApp</span>
              <span class="text-xs text-slate-300 font-medium">Pedido Directo</span>
            </div>
            <div class="bg-slateCard/80 border border-white/10 rounded-xl p-3 text-center">
              <span class="block text-white font-extrabold text-lg sm:text-xl">Hotel</span>
              <span class="text-xs text-slate-300 font-medium">&amp; Restaurante</span>
            </div>
          </div>
        </div>

        <!-- Columna Derecha: Logotipo Sticker Vectorial Destacado -->
        <div class="lg:col-span-5 flex flex-col items-center justify-center">
          <div class="relative p-6 sm:p-8 rounded-3xl bg-gradient-to-b from-slateCard to-slateDark border border-white/10 shadow-2xl">
            <!-- Detalle pincelada coral detrás del logo -->
            <div class="absolute inset-x-6 bottom-6 h-24 rounded-2xl bg-gradient-to-r from-marine/30 via-turquoise/25 to-coral/35 blur-xl"></div>
            <div data-arenas-logo="lg" class="relative w-64 h-64 sm:w-80 sm:h-80 logo-float drop-shadow-[0_18px_28px_rgba(0,0,0,0.65)]"></div>
            <div class="relative mt-4 text-center">
              <p class="text-xs uppercase tracking-widest text-slate-400 font-semibold">Pedidos y Reservaciones</p>
              <a
                href="https://wa.me/50489764449?text=Hola%20Arena's%20Hotel%20%26%20Restaurant%2C%20quisiera%20hacer%20una%20consulta."
                target="_blank"
                rel="noopener"
                class="inline-flex items-center gap-2 mt-1 text-emerald-400 hover:text-emerald-300 font-bold text-base transition-colors"
              >
                <span>WhatsApp: +504 8976-4449</span>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ===================================================================== -->
  <!-- MENÚ DIGITAL INTERACTIVO                                              -->
  <!-- ===================================================================== -->
  <section id="menu" class="py-16 sm:py-20">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Encabezado de Sección -->
      <div class="flex flex-col md:flex-row md:items-end justify-between gap-6 mb-10">
        <div>
          <span class="text-coral font-bold uppercase tracking-widest text-xs sm:text-sm">Carta Oficial • Precios en Lempiras (L.)</span>
          <h2 class="font-display text-3xl sm:text-4xl font-extrabold text-white mt-1">
            Nuestro Menú Digital
          </h2>
          <p class="text-slate-300 text-sm sm:text-base mt-2 max-w-2xl">
            Elige tu acompañamiento favorito (tajadas de plátano o papas fritas), tamaño o salsa directamente en cada platillo y agrégalo a tu pedido.
          </p>
        </div>

        <!-- Buscador en tiempo real -->
        <div class="w-full md:w-80 relative">
          <input
            type="text"
            id="menu-search"
            oninput="handleSearch(this.value)"
            placeholder="Buscar camarones, pescado, alitas..."
            class="w-full pl-11 pr-4 py-3 rounded-xl bg-slateCard border border-white/15 text-white placeholder-slate-400 text-sm focus:outline-none focus:border-turquoise focus:ring-2 focus:ring-turquoise/30 transition-all"
          />
          <svg class="w-5 h-5 text-slate-400 absolute left-3.5 top-1/2 -translate-y-1/2" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-4.35-4.35m0 0A7.5 7.5 0 104.5 4.5a7.5 7.5 0 0012.15 12.15z" />
          </svg>
        </div>
      </div>

      <!-- Barra de Filtros por Categoría -->
      <div id="category-filters" class="flex items-center gap-2.5 overflow-x-auto no-scrollbar pb-4 mb-8">
        <!-- Se renderiza dinámicamente con JS -->
      </div>

      <!-- Grid de Platillos -->
      <div id="menu-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        <!-- Tarjetas generadas dinámicamente por JavaScript -->
      </div>

      <!-- Mensaje cuando no hay resultados en búsqueda -->
      <div id="no-results" class="hidden text-center py-14 px-4 bg-slateCard rounded-2xl border border-white/10">
        <p class="text-lg font-bold text-white">No encontramos platillos con esa búsqueda</p>
        <p class="text-sm text-slate-400 mt-1">Intenta con otro término o selecciona "Todos" para ver el menú completo.</p>
        <button
          type="button"
          onclick="resetFilters()"
          class="mt-4 px-5 py-2.5 rounded-xl bg-turquoise text-white font-bold text-sm hover:opacity-90 transition-opacity"
        >
          Ver todo el menú
        </button>
      </div>
    </div>
  </section>

  <!-- ===================================================================== -->
  <!-- SECCIÓN DESTACADA: SOLO POR ENCARGO                                   -->
  <!-- ===================================================================== -->
  <section id="encargos" class="py-16 sm:py-20 bg-slateCard/70 border-y border-white/10 relative overflow-hidden">
    <div class="pointer-events-none absolute right-0 top-0 w-80 h-80 bg-coral/10 rounded-full blur-3xl"></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
      <div class="text-center max-w-3xl mx-auto mb-12">
        <span class="inline-block px-3.5 py-1 rounded-full bg-coral/20 border border-coral/40 text-coral text-xs font-extrabold uppercase tracking-widest">
          Preparación Especial Bajo Pedido Previo
        </span>
        <h2 class="font-display text-3xl sm:text-4xl font-extrabold text-white mt-3">
          Especialidades Solo por Encargo
        </h2>
        <p class="text-slate-300 text-sm sm:text-base mt-3">
          Ideales para familias, reuniones y grupos. Preparamos cada olla de sopa y cada parrillada al momento con ingredientes frescos del día para garantizar el máximo sabor.
        </p>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
        <!-- Tarjeta Especial 1: Parrilladas -->
        <div class="bg-slateDark rounded-3xl overflow-hidden border border-coral/40 shadow-xl flex flex-col sm:flex-row">
          <div class="sm:w-2/5 h-56 sm:h-auto relative">
            <img
              src="https://commons.wikimedia.org/wiki/Special:FilePath/Parrillada_Carne_asada.jpg?width=700"
              alt="Parrilladas Mixtas Arena's"
              onerror="handleImgError(this, 'Parrilladas Mixtas')"
              class="w-full h-full object-cover"
            />
            <span class="absolute top-3 left-3 px-3 py-1 rounded-lg bg-coral text-white text-xs font-extrabold uppercase shadow">
              Solo por Encargo
            </span>
          </div>
          <div class="p-6 sm:w-3/5 flex flex-col justify-between space-y-4">
            <div>
              <div class="flex items-start justify-between gap-2">
                <h3 class="font-display text-2xl font-extrabold text-white">Parrilladas Mixtas</h3>
                <span class="text-turquoise font-extrabold text-base sm:text-lg whitespace-nowrap">L. 1,000 – 2,500</span>
              </div>
              <p class="text-slate-300 text-sm mt-2 leading-relaxed">
                Abundante selección a la parrilla con <strong class="text-white">res, cerdo y pollo</strong>, acompañada de tajadas de plátano, frijoles fritos, queso, chismol, ensalada y encurtido.
              </p>
              <div class="flex flex-wrap gap-2 mt-3">
                <span class="px-2.5 py-1 rounded-lg bg-slateCard border border-white/10 text-xs font-bold text-slate-200">Familiar: L. 1,000</span>
                <span class="px-2.5 py-1 rounded-lg bg-slateCard border border-white/10 text-xs font-bold text-slate-200">Grupo: L. 2,000</span>
                <span class="px-2.5 py-1 rounded-lg bg-slateCard border border-white/10 text-xs font-bold text-slate-200">Evento: L. 2,500</span>
              </div>
            </div>
            <div class="flex flex-wrap gap-2.5 pt-2">
              <button
                type="button"
                onclick="quickAddS
