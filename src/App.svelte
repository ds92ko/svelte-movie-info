<script>
  import MoviesData from "./lib/movies";
  import Movies from "./lib/components/Movies.svelte";
  import Modal from "./lib/components/Modal.svelte";
  import NavBar from "./lib/components/NavBar.svelte";
  import TopBanner from "./lib/components/TopBanner.svelte";

  let data = [...MoviesData];
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

</script>

<NavBar />
<TopBanner />
<main class="container">
  <Movies {data} {handleLike} {handleOpenModal} />
  {#if isOpenModal}
    <Modal {data} {selectedMovie} {handleCloseModal} />
  {/if}
</main>
