<script>
  import { fly, fade } from "svelte/transition";
  
  let isOpenEvent = true;
  const handleToggleEvent = () => {
    isOpenEvent = !isOpenEvent;
  }

  export let banners = [];
  export let currentBanner = 0;
</script>

<div class="top-banner">
  {#if isOpenEvent}
    <div 
      class="banner"
      transition:fly={{ y: -100, duration: 300 }}
    >
      <p>{banners[currentBanner]}</p>
      <button on:click={handleToggleEvent}>X</button>
    </div>
  {:else}
    <div class="container">
      <button
        class="btn btn-banner"
        on:click={handleToggleEvent}
        in:fade
        out:fade
      >
        이벤트 창 열기
      </button>
    </div>
  {/if}
</div>

<style>
  .top-banner {
    position: absolute;
    top: 51px;
    width: 100%;

    .banner {
      position: absolute;
      width: 100%;
      top: 0;
      background: #666;
      padding: 5px 1em;
      display: flex;
      justify-content: space-between;
      align-items: center;
      color: #fff;
      text-align: center;
      margin-bottom: 1em;
      max-height: 100px;
      overflow: hidden;
      transition: all .3s;

      p {
        margin-bottom: 0;
      }

      button {
        padding: 2px;
      }
    }

    .btn-banner {
      position: absolute;
      top: 0;
    }
  }
</style>