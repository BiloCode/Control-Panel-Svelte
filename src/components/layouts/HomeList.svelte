<script>
  import { onDestroy } from "svelte";
  import { task_list } from '../../store/tasks';
  
  import Input from "../common/Input.svelte";
  import Task from "../common/Task.svelte";

  let name = '';
  let description = '';
  let list;

  const changeName = ev => (name = ev.detail);
  const changeDescription = ev => (description = ev.detail);
  
  const deleteTask = id => () => {
    task_list.update(list => list.filter(v => v.id !== id));
  }

  const createNewTask = ev => {
    if(!name || !description) return;

    const new_task = {
      id : list.length + 1,
      name,
      description
    }

    task_list.update(list => [...list, new_task]);

    name = '';
    description = '';
    ev.target.reset();
  }

  const unsubscribe = task_list.subscribe(value => (list = value));
  onDestroy(unsubscribe);

</script>

<div class="container">
  <div class="input-area">
    <form on:submit|preventDefault={createNewTask}>
      <Input text='Nombre de la tarea' on:change={changeName} />
      <Input type='textarea' text='Agregar descripcion' on:change={changeDescription} />
      <button class='add-task-button'>Ingresar Tarea</button>
    </form>
  </div>
  <div class="list-area">
    {#each list as task}
      <Task {...task} onDelete={deleteTask(task.id)} />
    {/each}
  </div>
</div>

<style lang="scss" >

  $padding : 2em;

  .container {
    width: 100%;
    height: 100%;
    display: grid;
    grid-template-columns: 350px 1fr;

    .input-area , .list-area {
      padding: 1em $padding;
      box-sizing: border-box;
    }
    
    .add-task-button {
      width: 100%;
      background-color: var(--color-secondary);
      color: #fff;
      outline: none;
      padding: 12px 8px;
      border: none;
      font-weight: bold;
      cursor: pointer;
      border-radius: 5px;
    }
  }

</style>