<template>
  <div
    v-if="$vuetify.breakpoint.mobile ? false : true"
    @mouseover="opciones = true"
    @mouseleave="opciones = false"
    class="text-gray-500 cursor-pointer"
  >
    <svg
      xmlns="http://www.w3.org/2000/svg"
      class="icon icon-tabler icon-tabler-report-money"
      width="40"
      height="40"
      viewBox="0 0 24 24"
      stroke-width="1.5"
      stroke="#000000"
      fill="none"
      stroke-linecap="round"
      stroke-linejoin="round"
    >
      <path stroke="none" d="M0 0h24v24H0z" fill="none" />
      <path
        d="M9 5h-2a2 2 0 0 0 -2 2v12a2 2 0 0 0 2 2h10a2 2 0 0 0 2 -2v-12a2 2 0 0 0 -2 -2h-2"
      />
      <rect x="9" y="3" width="6" height="4" rx="2" />
      <path d="M14 11h-2.5a1.5 1.5 0 0 0 0 3h1a1.5 1.5 0 0 1 0 3h-2.5" />
      <path d="M12 17v1m0 -8v1" />
    </svg>

    <div
      @mouseleave="opciones = false"
      @mouseover="opciones = true"
      class="absolute z-50 left-10 top-8 transition ease-in-out px-2"
      v-bind:class="{ hidden: !opciones, flex: opciones }"
    >
      <div class="bg-yellow-300 rounded-lg mt-4 shadow-lg">
        <span
          class="block font-bold text-xl px-6 text-neutral-900 py-2 bg-yellow-400"
          >Ventas</span
        >
        <v-list-item-title
          v-for="pagina in paginas"
          :key="pagina.id"
          class="my-0"
          ><nuxt-link
            class="text-decoration-none"
            :to="{ name: `${pagina.route_name}` }"
            ><p
              @click="opciones = false"
              class="text-neutral-900 px-6 py-2 my-0 hover:bg-neutral-800 hover:text-white"
            >
              {{ pagina.label }}
            </p></nuxt-link
          ></v-list-item-title
        >
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      opciones: true,
      paginas: [
        {
          id: 1,
          route_name: "notas_pedido",
          label: "Ver notas de pedido",
        },
        {
          id: 2,
          route_name: "cotizaciones",
          label: "Ver cotizaciones de clientes",
        },
        {
          id: 3,
          route_name: "productos",
          label: "Productos",
        },
      ],
    };
  },
};
</script>

<style></style>
