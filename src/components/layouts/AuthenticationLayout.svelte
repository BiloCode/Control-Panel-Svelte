<script>
  import NavigationMenu from './NavigationMenu.svelte';
</script>

<div class="main-layout">
  <NavigationMenu />
  <section class="screen-section" >
    <slot></slot>
  </section>
</div>

<style lang="scss">
  .main-layout {
    display: grid;
    grid-template-columns: 300px 1fr;

    .screen-section {
      width: 100%;
      height: 100vh;
      overflow: auto;
    }
  }
</style>