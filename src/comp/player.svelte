<script>
  export let music;
  export let artist;
  var tag = document.getElementById('targ')
  var firstScriptTag = document.getElementsByTagName("script")[0];
  firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);
  var player;
  function onYouTubeIframeAPIReady() {
    player = new YT.Player("player", {
      height: "360",
      width: "640",
      videoId: "M7lc1UVf-VE",
      events: {
        onReady: onPlayerReady,
      },
    });
  }

  // 4. The API will call this function when the video player is ready.
  function onPlayerReady(event) {
    event.target.playVideo();
  }
</script>
<svelte:head>
<script src="https://www.youtube.com/iframe_api" id="targ"></script>  
</svelte:head>

<div align="left" class="infos-container">
  <div align="left" class="infos">
    <h2 class="music">{music ?? "Não está tocando nada"}</h2>
    <h3 class="artist">{artist ?? "Não está tocando nada"}</h3>
  </div>
  <div id="player" />
</div>

<style type="text/css">
  * {
    box-sizing: border-box;
  }
  .infos-container {
    margin: 0;
    width: 100%;
    height: auto;
    display: inline-block;
    vertical-align: middle;
    align-items: left !important;
    background: rgb(26, 26, 26);
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
      Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  }

  .infos {
    transform: translate(10px, -2px);
  }
  .infos > .artist {
    font-size: 10px;
  }
  .infos > .music {
    font-size: 15px;
  }
</style>
