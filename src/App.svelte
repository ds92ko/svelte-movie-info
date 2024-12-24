<script>
  import MoviesData from "./lib/movies";
  import Movies from "./lib/components/Movies.svelte";
  import Modal from "./lib/components/Modal.svelte";
  import NavBar from "./lib/components/NavBar.svelte";
  import SearchBar from "./lib/components/SearchBar.svelte";
  import TopBanner from "./lib/components/TopBanner.svelte";

  let data = [...MoviesData];
  let searchData = [...data];
  let isOpenModal = false;
  /**
   * @type {number | null}
   */
  let selectedMovie = null;
  let errorMessage = '';
  /**
   * @param {number} id
   */
  const handleLike = (id) => {
    searchData = searchData.map(movie => {
      if (movie.id === id) {
        movie.likeCount += 1;
      }
      return movie;
    });
  }
  /**
   * @param {number} id
   */
  const handleOpenModal = (id) => {
    isOpenModal = true;
    selectedMovie = id;
  }
  const handleCloseModal = () => {
    isOpenModal = false;
    selectedMovie = null;
  } 
</script>

<NavBar />
<TopBanner />
<SearchBar {data} bind:searchData bind:errorMessage />
<main class="container">
  {#if errorMessage}
    <p class="error-message">{errorMessage}</p>
    {:else}
    <Movies data={searchData} {handleLike} {handleOpenModal} />
    {/if}
  {#if isOpenModal}
  <Modal data={searchData} {selectedMovie} {handleCloseModal} />
  {/if}
</main>

<style>
  .error-message {
    color: red;
  }
</style>