<script>
  import { enabledSpinner } from '../store/spinner';
  import { authenticationState } from '../store/authentication'

  import Input from "../components/common/Input.svelte";

	let username = '';
	let password = '';

	const onChangeUser = ev => (username = ev.detail);
	const onChangePassword = ev => (password = ev.detail);
  const onSubmit = () => {
    if(!username || !password) return;

    enabledSpinner.set(true);
	}

</script>

<div class="container">
  <h1 class="title" >Login de usuario</h1>
  <form on:submit|preventDefault={onSubmit}>
    <Input text='Usuario' on:change={onChangeUser} />
    <Input type='password' text='Contraseña' on:change={onChangePassword} />
    <button>Enviar</button>
  </form>
</div>

<style>

  .title {
    box-sizing: border-box;
    margin: 0;
    padding: 1em 0;
  }
	
	.container {
		width: 350px;
		height: 100vh;
		margin: 0 auto;
	}

</style>