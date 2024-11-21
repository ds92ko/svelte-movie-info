<script>
  import logo1 from './assets/svelte.svg';
  let logo2 = '/vite.svg';
  let textRed = "color: red;";
  const data = [
    { title: '고질라 X 콩: 뉴 엠파이어', year: 2024, category: '어드벤처, 액션, SF' },
    { title: '듄: 파트2', year: 2024, category: '액션' },
  ]
</script>

<main>
  <h1>영화정보</h1>
  <img src={logo1} alt="Svelte logo" />
  <img src={logo2} alt="Vite logo" />
  {#each data as { title, year, category }}
    <div>
      <h3 class="bg-yellow" style={textRed}>{title}</h3>
      <p>개봉: {year}</p>
      <p>장르: {category}</p>
    </div>
  {/each}
</main>

<style>
  .bg-yellow {
    background: yellow;
    padding: 10px;
  }
</style>
