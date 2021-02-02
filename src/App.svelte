<script>
	import { Router , Route } from 'svelte-routing';
	import { onDestroy, onMount } from "svelte";
	import { enabledSpinner } from './store/spinner';
	import { authenticationState } from './store/authentication';

	// Screens
	import Home from "./views/Home.svelte";
	import Login from "./views/Login.svelte";

	// Components
	import Spinner from "./components/common/Spinner.svelte";
	import BackgroundFixed from "./components/layouts/BackgroundFixed.svelte";
	import AuthenticationLayout from './components/layouts/AuthenticationLayout.svelte';
	
	let appState, isEnabledSpinner;

	const unsubscribe_auth = authenticationState.subscribe(value => (appState = value));
	const unsubscribe_spinner = enabledSpinner.subscribe(value => (isEnabledSpinner = value));

	onMount(() => {
		var token = localStorage.getItem('token');
		authenticationState.set(!token ? 'not-authenticated' : 'authenticated');
	});

	onDestroy(() => {
		unsubscribe_auth();
		unsubscribe_spinner();
	});

</script>

<main>
	{#if appState === 'not-authenticated'}
		<Router>
			<Route path="/" component={Login} />
		</Router>
	{:else if appState === 'authenticated'}
		<AuthenticationLayout>
			<Router>
				<Route path="/" component={Home} />
			</Router>
		</AuthenticationLayout>
	{/if}
</main>

{#if appState === 'loading' || isEnabledSpinner}
	<BackgroundFixed>
		<Spinner />
	</BackgroundFixed>
{/if}