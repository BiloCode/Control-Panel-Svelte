<script>
  import { createEventDispatcher } from "svelte";

  export let text;
  export let type = 'text';

  const dispatch = createEventDispatcher();
  const onInput = (ev) => {
    var value = ev.target.value;
    dispatch('change', value);
  }

</script>

<div class="input-container">
  <label class="input-label" for="">{text}</label>
  {#if type === 'textarea'}
    <textarea class='text-area' on:input={onInput} />
  {:else}
    <input {type} class='input' on:input={onInput}>
  {/if}
</div>

<style lang="scss" >
  
  .input-container {
    width: 100%;
    display: grid;
    margin-bottom: 1em;

    .input-label {
      padding-bottom: 5px;
      box-sizing: border-box;
    }

    .input , .text-area {
      background-color: var(--color-primary-light);
      border: none;
      padding: 8px;
      outline: none;
      color: #fff;
      font-family: var(--font);
    }

    .text-area {
      resize: none;
    }

    
  }

</style>