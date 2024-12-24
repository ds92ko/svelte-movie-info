<script>
  import { onMount } from "svelte";
  import MoviesData from "./lib/movies";
  import Movies from "./lib/components/Movies.svelte";
  import Modal from "./lib/components/Modal.svelte";
  import NavBar from "./lib/components/NavBar.svelte";
  import SearchBar from "./lib/components/SearchBar.svelte";
  import TopBanner from "./lib/components/TopBanner.svelte";

  let data = [...MoviesData];
  let searchData = [...data];
  let banners = [
    '영화 정보 업데이트',
    '신규 영화 추가',
    '이벤트 진행중'
  ]
  let currentBanner = 0;
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

  onMount(() => {
    setTimeout(() => {
      currentBanner += 1;
      console.log(currentBanner);
    }, 3000);
  })
</script>

<NavBar />
<TopBanner {banners} {currentBanner} />
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