<script>
  const elements = ["Archivo", "Edición", "Formato", "Ver", "Ayuda"];

  const elementsContent = {
    Archivo: ["Nuevo", "Abrir", "Guardar", "Guardar como", "Cerrar", "Salir"],
    Edición: [
      "Deshacer",
      "Rehacer",
      "Cortar",
      "Copiar",
      "Pegar",
      "Seleccionar todo",
    ],
    Formato: [
      "Fuente",
      "Tamaño de fuente",
      "Color de fuente",
      "Color de fondo",
    ],
    Ver: ["Zoom", "Pantalla completa"],
    Ayuda: ["Acerca de"],
  };

  let activeMenu = null;

  function handleMenuClick(element) {
    activeMenu = activeMenu === element ? null : element;
  }

  function handleMenuItemClick(menu, item) {
    window.alert(
      `Seleccionaste ${menu} > ${item}... No esta implementado para hacer algo útil 😅\nSolo disfrutalo`,
    );
    activeMenu = null;
  }
</script>

<div class="relative">
  <div class="p-2 border-b border-gray-300 text-sm bg-white">
    {#each elements as element}
      <div class="inline-block relative">
        <button
          type="button"
          class={`mx-2 rounded-t py-2 px-2 cursor-pointer ${
            activeMenu === element ? "bg-gray-100" : "hover:bg-gray-100"
          }`}
          on:click={() => handleMenuClick(element)}
          aria-haspopup="true"
          aria-expanded={activeMenu === element}
        >
          {element}
        </button>

        {#if activeMenu === element}
          <div
            class="absolute left-2 top-full mt-0.5 bg-white border border-gray-200 rounded shadow-lg z-50 min-w-40"
          >
            {#each elementsContent[element] as item}
              <button
                type="button"
                class="block w-full px-4 py-2 text-left text-sm hover:bg-gray-100"
                on:click={() => handleMenuItemClick(element, item)}
              >
                {item}
              </button>
            {/each}
          </div>
        {/if}
      </div>
    {/each}
  </div>
</div>
