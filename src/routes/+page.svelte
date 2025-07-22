<script>
  let x = 0.5;
  let y = 0.5;

  function handleMouseMove(e) {
    x = e.clientX / window.innerWidth;
    y = e.clientY / window.innerHeight;
    document.documentElement.style.setProperty('--x', x);
    document.documentElement.style.setProperty('--y', y);
  }
</script>

<svelte:window on:mousemove={handleMouseMove} />

<style>
  :global(body) {
    margin: 0;
    font-family: 'Segoe UI', sans-serif;
    background: #0f1117;
    color: #cdd6f4;
    overflow: hidden;
  }

  .bg {
    position: fixed;
    width: 200%;
    height: 200%;
    top: -50%;
    left: -50%;
    background: conic-gradient(
      from 0deg at calc(var(--x, 0.5) * 100%) calc(var(--y, 0.5) * 100%),
      #89b4fa,
      #f5c2e7,
      #a6e3a1,
      #89b4fa
    );
    animation: rotate 20s linear infinite;
    filter: blur(160px);
    opacity: 0.3;
    z-index: 0;
  }

  @keyframes rotate {
    from {
      transform: rotate(0deg) scale(1.2);
    }
    to {
      transform: rotate(360deg) scale(1.2);
    }
  }

  .content {
    position: relative;
    z-index: 1;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  h1 {
    font-size: 3rem;
    color: #89b4fa;
  }

  a {
    font-size: 1.25rem;
    color: #f5c2e7;
    text-decoration: none;
  }
</style>

<div class="bg"></div>

<div class="content">
  <h1>Coming Soon</h1>
  <a href="https://notes.aslamcodes.in" target="_blank">
    Meanwhile check out my <span style="text-decoration: underline;">notes</span> page
  </a>
</div>
