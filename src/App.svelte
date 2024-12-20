<script>
  const data = [
    { title: '파묘', year: 2024, category: '미스터리, 공포', likeCount: 0},
    { title: '고질라 X 콩: 뉴 엠파이어', year: 2024, category: '어드벤처, 액션, SF', likeCount: 0 },
    { title: '듄: 파트2', year: 2024, category: '액션', likeCount: 0 },
  ]
  
  /**
   * @param {number} index
   */
  const handleLike = (index) => {
    data[index].likeCount += 1;
  }
</script>

<main>
  <h1>영화정보</h1>
  {#each data as { title, year, category, likeCount }, index}
    <div>
      <h3 class="bg-yellow">{title}</h3>
      <p>개봉: {year}</p>
      <p>장르: {category}</p>
      <button on:click={() => handleLike(index)}>좋아요 {likeCount}</button>
    </div>
  {/each}
</main>

<style>
  .bg-yellow {
    background: yellow;
    padding: 10px;
    color: #333;
  }
</style>
