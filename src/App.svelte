<script>
  import Player from "./comp/player.svelte";
  import Songs from "./comp/songs.svelte";
  let selected = undefined;
  let playlist = [];
  function Tools() {
    function setUser(user) {
      // user = username do usuario
      
      let i = localStorage.setItem('token');
      let j = localStorage.setItem('username', user)
      return i
    } 
    function getItem (id) {
      let i = localStorage.getItem(id);
      return i
    }
    return {
      getItem,
      setUser,
    };
  }
  var tools = new Tools();
  function User() {
    let infos = [];
    function isLogged() {
      k = tools.getItem('user')
      if (k != null) { return true; } else { return false; }
    }
    function name() {
      let i = tools.getCookie("user-name");
      infos["name"] = i;
      return i;
    }
    function login(username) {
      tools.setUser(username)
    }

    /* chamando as funções de forma estatica */
    isLogged();
    name();

    return infos;
  }
  let user = new User();
</script>

<body>
<header>
  {#if user.login}
    <h2>Olá {user.name}</h2>
  {:else}
    <h2>Olá, Usuario, Por favor registre-se :)</h2>
  {/if}
</header>
<Songs {selected} />
<footer>
  <Player />
</footer>
  
</body>
<style>
  footer {
    padding: 0%;
    bottom: 1;
    top: -1;
    left: 0;
    right: 0;
  }
</style>
