<script>
  const data = [
    { title: '파묘', year: 2024, category: '미스터리, 공포', likeCount: 0, imgUrl: '/images/파묘.jpg' },
    { title: '고질라 X 콩: 뉴 엠파이어', year: 2024, category: '어드벤처, 액션, SF', likeCount: 0, imgUrl: '/images/고질라x콩.jpg' },
    { title: '듄: 파트2', year: 2024, category: '액션', likeCount: 0, imgUrl: '/images/듄-파트2.jpg' },
  ]
  
  /**
   * @param {number} index
   */
  const handleLike = (index) => {
    data[index].likeCount += 1;
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
        <button on:click={() => handleLike(index)}>좋아요 {likeCount}</button>
      </div>
    </div>
  {/each}
</main>

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
