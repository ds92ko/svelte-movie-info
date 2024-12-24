<script>
  let keyword = '';
  export let data = [];
  export let searchData = [];
  export let errorMessage = '';

  $: if (keyword.length > 16) {
    errorMessage = '검색어는 16자 이하로 입력해주세요.';
  } else {
    errorMessage = '';
  }

const searchMovies = () => {
  if (!keyword) {
    errorMessage = '검색어를 입력해주세요.';
    return;
  }

  searchData = data.filter(movie => movie.title.includes(keyword));

  if (searchData.length === 0) {
    errorMessage = '검색 결과가 없습니다.';
  } else {
    errorMessage = '';
  }
}

const resetSearch = () => {
  keyword = '';
  searchData = [...data];
  errorMessage = '';
}
</script>

<div class="search-box">
  <div class="input-group">
    <input
      type="search"
      placeholder="영화 제목을 입력하세요."
      bind:value={keyword}
      on:keydown={(e) => {
        if (e.key === 'Enter') {
          searchMovies();
        }
      }}
    />
    <button on:click={searchMovies}>검색</button>
    <button on:click={resetSearch}>초기화</button>
  </div>
</div>

<style>
  .search-box {
    padding-inline: 20px;
    margin-block: 20px;

    .input-group {
      display: flex;
      width: 100%;
      border: 1px solid #ccc;
    }

    input {
      flex-grow: 1;
      width: 100%;
      border: none;
      outline: none;
      padding: 10px;
    }

    button {
      display: block;
      flex-shrink: 0;
      border: none;
      outline: none;
      background: #666;
      color: #fff;
      padding: 10px;
      height: 100%;
      margin: 0;
      border-left: 1px solid #ccc;
    }
  }
</style>