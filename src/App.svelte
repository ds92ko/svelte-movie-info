<script>
  import MoviesData from "./lib/movies";
  import Movies from "./lib/components/Movies.svelte";
  import Modal from "./lib/components/Modal.svelte";
  import NavBar from "./lib/components/NavBar.svelte";

  let data = [...MoviesData];
  let isOpenEvent = true;
  let isOpenModal = false;
  /**
   * @type {number | null}
   */
  let selectedMovie = null;
  /**
   * @param {number} index
   */
  const handleLike = (index) => {
    data[index].likeCount += 1;
  }
  /**
   * @param {number} index
   */
  const handleOpenModal = (index) => {
    isOpenModal = true;
    selectedMovie = index;
  }
  const handleCloseModal = () => {
    isOpenModal = false;
    selectedMovie = null;
  } 
  const handleCloseEvent = () => {
    isOpenEvent = !isOpenEvent;
  }
</script>

<NavBar />
<div class={`event ${isOpenEvent ? 'show' : ''}`}>
  <p>NETFLIX 강렬한 운명의 드라마, 경기크리처</p>
  <button on:click={handleCloseEvent}>X</button>
</div>
<Movies {data} {handleLike} {handleOpenModal} />
{#if isOpenModal}
  <Modal {data} {selectedMovie} {handleCloseModal} />
{/if}

<style>
  .event {
    width: 100%;
    background: #666;
    padding: 5px 1em;
    display: flex;
    justify-content: space-between;
    align-items: center;
    color: #fff;
    text-align: center;
    margin-bottom: 1em;

    max-height: 0;
    opacity: 0;
    overflow: hidden;
    transition: all .3s;

    &.show {
      max-height: 100px;
      opacity: 1;
    }

    p {
      margin-bottom: 0;
    }

    button {
      padding: 2px;
    }
  }
</style>