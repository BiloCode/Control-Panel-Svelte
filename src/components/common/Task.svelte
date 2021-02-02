<script>
  export let id, name, description, onDelete;
</script>

<div class="list-item-container" >
  <span class="id">#{id}</span>
  <span class="name">{name}</span>
  <span class="description">{description}</span>
  <div class="action-buttons-container">
    <button class="delete-button" on:click={onDelete}>Eliminar</button>
  </div>
</div>

<style lang="scss" >

  .list-item-container {
    display: grid;
    grid-template-columns: 32px 200px 1fr 1fr;
    justify-items: center;
    align-items: center;
    box-sizing: border-box;
    padding: 0.5em 0;
    border-bottom: 1px solid rgb(230,230,230);

    .id {
      font-weight: bold;
    }

    .description {
      justify-self: flex-start;
      font-style: italic;
    }

    .delete-button {
      margin : 0;
      color: #fff;
      cursor: pointer;
      font-weight: bold;
      background-color: rgb(230, 0, 0);
      padding: 5px 1em;
      border: none;
      border-radius: 5px;
    }
  }

</style>
