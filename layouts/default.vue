<template>
  <div class="body">
    <Header />
    <div class="container">
      <slot />
    </div>
    <Footer class="footer" />
  </div>
</template>

<style>
.body {
  height: 100vh;
}
.container {
  padding: 10px;
}
.footer {
  position: sticky;
  top: 100vh;
  width: 100%;
}
</style>
