<header class="header">
  <nav>
    <ul class="nav-list">
      <li class="nav-item">
        <a href="/" class="nav-link">Home</a>
      </li>
      <li class="nav-item">
        <a href="/about" class="nav-link">About</a>
      </li>
      <li class="nav-item">
        <a href="/contact" class="nav-link">Contact</a>
      </li>
    </ul>
  </nav>
</header>

<style>
  .header {
    position: relative;
    background: #333;
    color: #fff;
    padding: 1rem;
    z-index: 100;
    margin-bottom: 100px;
  }

  .nav-list {
    display: flex;
    justify-content: center;
    list-style: none;

    .nav-item {
      margin-right: 1rem;

      .nav-link {
        color: #fff;
        text-decoration: none;
      }
    }
  }
</style>