<div class="background-fixed">
  <div class="spinner-container">
    <slot></slot>
  </div>
</div>

<style lang="scss">

  .background-fixed {
    width: 100%;
    height: 100vh;
    background-color: rgba(0,0,0,.8);
    z-index: 1;
    position: fixed;
    top: 0;
    left: 0;

    .spinner-container {
      width: max-content;
      height: max-content;
      margin: auto;
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
    }
  }

</style>