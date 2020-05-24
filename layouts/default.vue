<template>
  <div>
    <nav
      class="font-sans bg-white text-center flex justify-between my-4 mx-auto container overflow-hidden"
    >
      <a href="/" class="block text-left">
        Nuxt Content Blog
      </a>
      <ul class="text-sm text-gray-700 list-none p-0 flex items-center">
        <li>
          <a
            href="#"
            class="inline-block py-2 px-3 text-gray-900 hover:text-gray-700 no-underline"
            >Github</a
          >
        </li>
        <li>
          <a
            href="#"
            class="inline-block py-2 px-3 text-gray-900 hover:text-gray-700 no-underline"
            >Tutorial</a
          >
        </li>
        <li class="pr-2">
          <a
            href="#"
            class="inline-block py-2 px-3 text-gray-900 hover:text-gray-700 no-underline"
            >Acerca de</a
          >
        </li>
      </ul>
    </nav>
    <section
      class="font-sans container m-auto flex flex-col py-8 max-w-xl text-left px-6"
    >
      <nuxt />
    </section>
  </div>
</template>
