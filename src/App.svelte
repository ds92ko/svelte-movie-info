<script>
  import data from "./lib/movies";

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

<main class="container">
  <h1>영화정보</h1>
  {#each data as { title, year, category, likeCount, imgUrl }, index}
    <div class="movie">
      <figure>
        <img src={imgUrl} alt={title} />
      </figure>
      <div class="info">
        <h3 class="bg-yellow">{title}</h3>
        <p>개봉: {year}</p>
        <p>장르: {category}</p>
        <button class="btn" on:click={() => handleLike(index)}>좋아요 {likeCount}</button>
        <button class="btn btn-primary" on:click={() => handleOpenModal(index)}>상세보기</button>
      </div>
    </div>
  {/each}
</main>

{#if isOpenModal}
  <div class="modal">
    <div class="inner">
      <h3>{data[selectedMovie].title}</h3>
      <p>{@html data[selectedMovie].story}</p>
      <button class="btn btn-close" on:click={handleCloseModal}>닫기</button>
    </div>
  </div>
{/if}

<style>
  .bg-yellow {
    background: yellow;
    padding: 10px;
    color: #333;
  }

  .movie {
    width: 100%;
    border: 1px solid #ccc;
    display: flex;
    margin-bottom: 20px;
    padding: 1rem;

    figure {
      width: 30%;
      margin-right: 1rem;
    }

    img {
      width: 100%;
    }

    .info {
      width: 100%;
    }
  }

  .modal {
    background: rgba(0, 0, 0, 0.7);
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;

    .inner {
      background: #fff;
      width: 80%;
      padding: 20px;
      border-radius: 10px;
    }
  }
</style>
