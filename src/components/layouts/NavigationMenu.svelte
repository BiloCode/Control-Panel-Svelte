<script>
  import { navigate } from 'svelte-routing';
  import { FaHome, FaList, FaEuroSign } from 'svelte-icons/fa';

  import NavigationItem from '../common/NavigationItem.svelte';
  import NavigationLogout from '../common/NavigationLogout.svelte';

  const NavigateToScreen = path => () => navigate(path);
</script>

<nav>
  <header>
    <h1>Panel de Control</h1>
  </header>
  <section>
    <ul class="navigation-list" >
      <NavigationItem Icon={FaHome} name="Inicio" onClick={NavigateToScreen("/")} />
      <NavigationItem Icon={FaEuroSign} name="Pagos" onClick={NavigateToScreen("/payments")} />
      <NavigationItem Icon={FaList} name="Actividades" onClick={NavigateToScreen("/activities")} />
    </ul>
    <NavigationLogout />
  </section>
</nav>

<style lang="scss">
  nav {
    --header-height: 120px;

    width: 100%;
    height: 100vh;
    box-sizing: border-box;
    background-color: var(--color-primary-dark);

    header {
      height: var(--header-height);
      display: flex;
      justify-content: center;
      align-items: center;

      h1 {
        margin: 0;
        padding: .5em 0;
        font-size: 1.8em;
        font-weight: bolder;
        box-sizing: border-box;
      }
    }

    section {
      height: calc(100vh - var(--header-height));
      display: grid;
      grid-template-rows: 1fr max-content;
    }

    .navigation-list {
      padding: 0;
      margin: 0;
      list-style: none;
    }

  }
  
</style>