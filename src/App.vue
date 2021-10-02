<template>
  <div>
    <header class="bg-white shadow" v-if="$route.meta.title">
      <div class="px-4 py-6 mx-auto max-w-7xl sm:px-6 lg:px-8">
        <h1
          class="text-3xl font-bold leading-tight text-primary"
        >
          {{ $route.meta.title }}
        </h1>
      </div>
    </header>
    <main class="m-6">
      <router-view />
    </main>
  </div>
</template>
