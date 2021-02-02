<script>

  export var Icon;
  export var name = "";
  export var onClick;

</script>

<li class="item" on:click={onClick} >
  <span class="icon">
    <Icon />
  </span>
  <span class="name">{name}</span>
</li>

<style lang="scss">
  
  .item {
    width: 100%;
    padding: 1em 2em;
    box-sizing: border-box;
    border-bottom: 1px solid var(--color-primary-light);
    display: flex;
    align-items: center;
    cursor: pointer;
    
    .icon { 
      width: 20px;
      height: 20px;
    }

    .name {
      font-weight: 500;
      padding-left: 1em;
      box-sizing: border-box;
    }

    &:hover , &.selected {
      background-color: var(--color-primary-light);
      color: #fff;
    }

  }

</style>