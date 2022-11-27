<script>
  import Player from "./comp/player.svelte";
  import Songs from "./comp/songs.svelte";
  let selected = undefined;
  let playlist = [];
  class User {
    constructor () {
      this.user = localStorage.getItem('user') || undefined;
    }
    isLogged() {
      if (this.user) return true || false;
    }
    get name() {
      return this.user;
    }
    login(username) {
      localStorage.setItem("user", username)
    }
    logout() {
      localStorage.removeItem("user")
    }
  }

  let user = new User();
</script>

<body>
<header>
  {#if user.isLogged()} 
    <h2>Olá {user.name}</h2>
    <button on:click={user.logout()}>logout</button>
  {:else}
    <h2>Olá, Usuario, Por favor registre-se :D</h2>
    <button on:click={user.login("HELLO")}> registrar</button>
  {/if}
</header>

<footer>
</footer>
  
</body>
<style>
  
</style>
