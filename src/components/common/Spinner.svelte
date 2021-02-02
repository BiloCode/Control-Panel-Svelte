<div class="spinner"></div>

<style>

  .spinner {
    width: 48px;
    height: 48px;
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    line-height: 0;
    border-radius: 50%;
    border: 4px solid rgb(48, 48, 48);
    border-bottom-color: rgb(99, 99, 99);
    animation: spinner-loading .5s linear infinite;
  }

  @keyframes spinner-loading {
    to {
      transform: rotate(1turn);
    }
  }

</style>