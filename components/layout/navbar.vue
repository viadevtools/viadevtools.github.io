<template>
  <div id="navbar">
    <div class="dark:bg-black bg-slate-100 dark:text-gray-300 light:text-black" style="position: sticky;top: 0px;z-index: 999">

      <!-- PC -->
      <div class="mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex h-16 items-center justify-between">
          <div class="flex items-center">
            <div class="flex-shrink-0">
              <h1>Via Dev Tools</h1>
            </div>

            <!--          <div class="hidden md:block">-->
            <!--            <div class="ml-10 flex items-baseline space-x-4">-->
            <!--              <a v-for="item in navigation" :key="item.name" :href="item.href" :class="[item.current ? 'bg-gray-900 text-white' : 'dark:text-gray-300 hover:bg-gray-700 light:text-black hover:text-white', 'px-3 py-2 rounded-md text-sm font-medium']" :aria-current="item.current ? 'page' : undefined">{{ item.name }}</a>-->
            <!--            </div>-->
            <!--          </div>-->
          </div>
          <div class="md:block" style="width: 50%">
            <input v-model="dataSearch" placeholder="Search tools..." class="block w-full px-3 py-2 transition duration-100 ease-in-out border rounded shadow-sm focus:ring-2 focus:ring-blue-500 focus:outline-none focus:ring-opacity-50 disabled:opacity-50 disabled:cursor-not-allowed">
          </div>
          <div class="md:block">
            <div class="ml-4 flex items-center md:ml-6">
              <button type="button" @click="setColorTheme($colorMode.preference == 'dark' ? 'light' : 'dark')" class="rounded-full bg-gray-800 p-1 text-gray-400 hover:text-white focus:outline-none focus:ring-2 focus:ring-white focus:ring-offset-2 focus:ring-offset-gray-800">
                <span class="md:block">
                  <svg v-if="$colorMode.value == 'dark'" xmlns="http://www.w3.org/2000/svg"
                       class="h-6 w-6 text-gray-50 hidden lg:block hover:dark:text-yellow-400 hover:text-yellow-400"
                       viewBox="0 0 20 20"
                       fill="currentColor">
                    <path d="M17.293 13.293A8 8 0 016.707 2.707a8.001 8.001 0 1010.586 10.586z" />
                  </svg>
                  <svg v-if="$colorMode.value == 'light'" xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 hidden lg:block hover:dark:text-yellow-400 hover:text-yellow-400"
                       viewBox="0 0 20 20" fill="currentColor ">
                    <path fill-rule="evenodd"
                          d="M10 2a1 1 0 011 1v1a1 1 0 11-2 0V3a1 1 0 011-1zm4 8a4 4 0 11-8 0 4 4 0 018 0zm-.464 4.95l.707.707a1 1 0 001.414-1.414l-.707-.707a1 1 0 00-1.414 1.414zm2.12-10.607a1 1 0 010 1.414l-.706.707a1 1 0 11-1.414-1.414l.707-.707a1 1 0 011.414 0zM17 11a1 1 0 100-2h-1a1 1 0 100 2h1zm-7 4a1 1 0 011 1v1a1 1 0 11-2 0v-1a1 1 0 011-1zM5.05 6.464A1 1 0 106.465 5.05l-.708-.707a1 1 0 00-1.414 1.414l.707.707zm1.414 8.486l-.707.707a1 1 0 01-1.414-1.414l.707-.707a1 1 0 011.414 1.414zM4 11a1 1 0 100-2H3a1 1 0 000 2h1z"
                          clip-rule="evenodd" />
                  </svg>
                </span>
              </button>
              <!--            <button type="button" class="rounded-full bg-gray-800 p-1 text-gray-400 hover:text-white focus:outline-none focus:ring-2 focus:ring-white focus:ring-offset-2 focus:ring-offset-gray-800">-->
              <!--              <span class="sr-only">View notifications</span>-->
              <!--              <BellIcon class="h-6 w-6" aria-hidden="true" />-->
              <!--            </button>-->

              <!--            &lt;!&ndash; Profile dropdown &ndash;&gt;-->
              <!--            <Menu as="div" class="relative ml-3">-->
              <!--              <div>-->
              <!--                <MenuButton class="flex max-w-xs items-center rounded-full bg-gray-800 text-sm focus:outline-none focus:ring-2 focus:ring-white focus:ring-offset-2 focus:ring-offset-gray-800">-->
              <!--                  <span class="sr-only">Open user menu</span>-->
              <!--                  <img class="h-8 w-8 rounded-full" :src="user.imageUrl" alt="" />-->
              <!--                </MenuButton>-->
              <!--              </div>-->
              <!--              <transition enter-active-class="transition ease-out duration-100" enter-from-class="transform opacity-0 scale-95" enter-to-class="transform opacity-100 scale-100" leave-active-class="transition ease-in duration-75" leave-from-class="transform opacity-100 scale-100" leave-to-class="transform opacity-0 scale-95">-->
              <!--                <MenuItems class="absolute right-0 z-10 mt-2 w-48 origin-top-right rounded-md bg-white py-1 shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none">-->
              <!--                  <MenuItem v-for="item in userNavigation" :key="item.name" v-slot="{ active }">-->
              <!--                    <a :href="item.href" :class="[active ? 'bg-gray-100' : '', 'block px-4 py-2 text-sm text-gray-700']">{{ item.name }}</a>-->
              <!--                  </MenuItem>-->
              <!--                </MenuItems>-->
              <!--              </transition>-->
              <!--            </Menu>-->
            </div>
          </div>
          <!--        <div class="-mr-2 flex md:hidden">-->
          <!--          &lt;!&ndash; Mobile menu button &ndash;&gt;-->
          <!--          <DisclosureButton class="inline-flex items-center justify-center rounded-md bg-gray-800 p-2 text-gray-400 hover:bg-gray-700 hover:text-white focus:outline-none focus:ring-2 focus:ring-white focus:ring-offset-2 focus:ring-offset-gray-800">-->
          <!--            <span class="sr-only">Open main menu</span>-->
          <!--            <Bars3Icon v-if="!open" class="block h-6 w-6" aria-hidden="true" />-->
          <!--            <XMarkIcon v-else class="block h-6 w-6" aria-hidden="true" />-->
          <!--          </DisclosureButton>-->
          <!--        </div>-->
        </div>
      </div>

      <!-- Mobile -->
      <!--    <DisclosurePanel class="md:hidden">-->
      <!--      <div class="space-y-1 px-2 pt-2 pb-3 sm:px-3">-->
      <!--        <DisclosureButton v-for="item in navigation" :key="item.name" as="a" :href="item.href" :class="[item.current ? 'bg-gray-900 text-white' : 'text-gray-300 hover:bg-gray-700 hover:text-white', 'block px-3 py-2 rounded-md text-base font-medium']" :aria-current="item.current ? 'page' : undefined">{{ item.name }}</DisclosureButton>-->
      <!--      </div>-->
      <!--      <div class="border-t border-gray-700 pt-4 pb-3">-->
      <!--        <div class="flex items-center px-5">-->
      <!--          <div class="flex-shrink-0">-->
      <!--            <img class="h-10 w-10 rounded-full" :src="user.imageUrl" alt="" />-->
      <!--          </div>-->
      <!--          <div class="ml-3">-->
      <!--            <div class="text-base font-medium leading-none text-white">{{ user.name }}</div>-->
      <!--            <div class="text-sm font-medium leading-none text-gray-400">{{ user.email }}</div>-->
      <!--          </div>-->
      <!--          <button type="button" class="ml-auto flex-shrink-0 rounded-full bg-gray-800 p-1 text-gray-400 hover:text-white focus:outline-none focus:ring-2 focus:ring-white focus:ring-offset-2 focus:ring-offset-gray-800">-->
      <!--            <span class="sr-only">View notifications</span>-->
      <!--            <BellIcon class="h-6 w-6" aria-hidden="true" />-->
      <!--          </button>-->
      <!--        </div>-->
      <!--        <div class="mt-3 space-y-1 px-2">-->
      <!--          <DisclosureButton v-for="item in userNavigation" :key="item.name" as="a" :href="item.href" class="block rounded-md px-3 py-2 text-base font-medium text-gray-400 hover:bg-gray-700 hover:text-white">{{ item.name }}</DisclosureButton>-->
      <!--        </div>-->
      <!--      </div>-->
      <!--    </DisclosurePanel>-->

    </div>
    <div v-if="dataSearch"
        class="md:block" style="display: flex;justify-content: center;position: fixed;top: 65px;width: 100%">
      <div class="dark:bg-black bg-slate-100" style="width: 50%;padding: 15px;border-radius: 10px;z-index: 99999">
        <div class="grid grid-cols-1 gap-y-10 gap-x-6 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 xl:gap-x-8">
          <a v-for="product in products" :key="product.id" :href="product.href" class="group">
            <div class="aspect-w-1 aspect-h-1 w-full overflow-hidden rounded-lg bg-gray-200 xl:aspect-w-7 xl:aspect-h-8">
              <img :src="product.imageSrc" :alt="product.imageAlt" class="h-full w-full object-cover object-center" />
            </div>
            <h3 class="mt-4 text-sm text-gray-700">{{ product.name }}</h3>
            <p class="mt-1 text-lg font-medium text-gray-900">{{ product.price }}</p>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import {ref, watch, computed} from 'vue'

const dataSearch = ref('');

watch (dataSearch, (val) => {
  console.log(val)
})
let dataProduct = computed(() => {

})
const colorMode = useColorMode()

const setColorTheme = (newTheme: any) => {
  colorMode.preference = newTheme
}

const user = {
  name: 'Tom Cook',
  email: 'tom@example.com',
  imageUrl:
      'https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80',
}
const navigation = [
  { name: 'Dashboard', href: '#', current: true },
  { name: 'Team', href: '#', current: false },
  { name: 'Projects', href: '#', current: false },
  { name: 'Calendar', href: '#', current: false },
  { name: 'Reports', href: '#', current: false },
]
const userNavigation = [
  { name: 'Your Profile', href: '#' },
  { name: 'Settings', href: '#' },
  { name: 'Sign out', href: '#' },
]
const products = [
  {
    id: 1,
    name: 'Earthen Bottle',
    href: '#',
    price: '$48',
    imageSrc: 'https://tailwindui.com/img/ecommerce-images/category-page-04-image-card-01.jpg',
    imageAlt: 'Tall slender porcelain bottle with natural clay textured body and cork stopper.',
  },
  {
    id: 2,
    name: 'Nomad Tumbler',
    href: '#',
    price: '$35',
    imageSrc: 'https://tailwindui.com/img/ecommerce-images/category-page-04-image-card-02.jpg',
    imageAlt: 'Olive drab green insulated bottle with flared screw lid and flat top.',
  },
  {
    id: 3,
    name: 'Focus Paper Refill',
    href: '#',
    price: '$89',
    imageSrc: 'https://tailwindui.com/img/ecommerce-images/category-page-04-image-card-03.jpg',
    imageAlt: 'Person using a pen to cross a task off a productivity paper card.',
  },
  {
    id: 4,
    name: 'Machined Mechanical Pencil',
    href: '#',
    price: '$35',
    imageSrc: 'https://tailwindui.com/img/ecommerce-images/category-page-04-image-card-04.jpg',
    imageAlt: 'Hand holding black machined steel mechanical pencil with brass tip and top.',
  },
  // More products...
]
</script>