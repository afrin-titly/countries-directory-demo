<template>
  <nav
    class="
      relative
      flex flex-wrap
      items-center
      justify-between
      px-2
      py-3
      bg-indigo-500
      mb-3
    "
  >
    <div
      class="container px-4 mx-auto flex flex-wrap items-center justify-between"
    >
      <div
        class="
          w-full
          relative
          flex
          justify-between
          lg:w-auto
          px-4
          lg:static
          lg:block
          lg:justify-start
        "
      >
        <a
          class="
            text-sm
            font-bold
            leading-relaxed
            inline-block
            mr-4
            py-2
            whitespace-nowrap
            uppercase
            text-white
            flex
          "
          href="/"
        >
          <img class="w-12 mr-2" src="/assets/icon.png" alt="" />
          <span class="mx-1 my-3"> Countries  </span>
        </a>
        <button
          class="
            text-white
            cursor-pointer
            text-xl
            leading-none
            px-3
            py-1
            border border-solid border-transparent
            rounded
            bg-transparent
            block
            lg:hidden
            outline-none
            focus:outline-none
          "
          type="button"
          v-on:click="toggleNavbar()"
        >
          <i class="fas fa-bars"></i>
        </button>
      </div>
      <div
        v-bind:class="{ hidden: !showMenu, flex: showMenu }"
        class="lg:flex lg:flex-grow items-center"
      >
        <ul class="flex flex-col lg:flex-row list-none ml-auto">
          <li class="nav-item">
            <router-link to="/">
              <span class="text-white font-semibold px-3 py-2 item-center flex"
                >Home</span
              >
            </router-link>
          </li>
          <li class="nav-item">
            <router-link to="/about">
              <span class="text-white font-semibold px-3 py-2 item-center flex"
                >About</span
              >
            </router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: "Navbar",
  data() {
    return {
      showMenu: false,
    };
  },
  methods: {
    toggleNavbar: function () {
      this.showMenu = !this.showMenu;
    },
  },
};
</script>