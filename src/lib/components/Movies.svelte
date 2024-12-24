<script>
  export let data = [];
  export let handleLike;
  export let handleOpenModal;
</script>

<h1>영화정보</h1>
{#each data as { id, title, year, category, likeCount, imgUrl }}
  <div class="movie">
    <figure>
      <img src={imgUrl} alt={title} />
    </figure>
    <div class="info">
      <h3 class="bg-yellow">{title}</h3>
      <p>개봉: {year}</p>
      <p>장르: {category}</p>
      <button class="btn" on:click={() => handleLike(id)}>좋아요 {likeCount}</button>
      <button class="btn btn-primary" on:click={() => handleOpenModal(id)}>상세보기</button>
    </div>
  </div>
{/each}

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
</style>